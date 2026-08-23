---
name: karmacheck-track-and-adjudicate-case
description: >-
  Track a KarmaCheck case to completion, read individual screening results, retrieve the report PDF,
  and drive the adjudication and pre-adverse-action workflow. Use this after a case has been ordered
  and you need to act on results.
api: KarmaCheck API
generated: '2026-08-23'
method: generated
source: >-
  openapi/karmacheck-api-openapi.yml +
  https://developer.karmacheck.com/background-check-api/overview/case-lifecycle +
  https://developer.karmacheck.com/background-check-api/overview/service-lifecycle
operations:
  - get-case-id-caseid
  - get-case-id-caseId-services
  - get-case-id-caseid-data-servicetypeid
  - get-case-id-caseId-data-serviceId-pdf
  - get-case-id-caseId-data-serviceId-pdf-download
  - get-caseid-caseId-report-pdf-download-url
  - put-case-id-caseId-action-beginprocessing
  - put-case-id-caseId-action-place
  - post-case-id-caseId-action-preadverse
  - get-case-id-caseId-preadverse-type-pdf
  - get-case-id-caseId-preadverse-type-pdf-download
  - post-case-archive-caseId
  - post-case-unarchive-caseId
---

# Track a case and act on the result

## The status model

A case carries a **primary status**, a **secondary status** and a **result type**. Primary statuses
are `Pending`, `Blocked`, `Complete`, `Consider`, `Adjudicated`, `Placed` and `Canceled`. Each
individual screening (a *case data* record) also has its own status track, and the two do not move
in lockstep.

`GET /case/id/{caseId}` (`get-case-id-caseid`) gives the case. `GET /case/id/{caseId}/services`
(`get-case-id-caseId-services`) gives per-screening progress.

## Reading a screening result

`GET /case/id/{caseId}/data/{serviceTypeId}` (`get-case-id-caseid-data-servicetypeid`) returns the
case data for a screening type.

Case data is **polymorphic**: one record carries exactly one of 22 `Details*` payloads chosen by
service category — `DetailsSSN`, `DetailsNationalCriminal`, `DetailsCountyCriminal`,
`DetailsMotorVehicle`, `DetailsEducation`, `DetailsEmployment`, `DetailsDrug`, `DetailsOHS`,
`DetailsOIG`, `DetailsSexOffender` and others. Branch on the service category before reading fields.

Screening outcomes are `clear`, `consider` and `acknowledge`. These are **results, not errors** —
they arrive with HTTP 200.

## Documents

- `GET /case/id/{caseId}/data/{serviceId}/pdf` and `.../pdf/download` — per-screening PDF.
- `GET /case/id/{caseId}/report/pdf/download/url` (`get-caseid-caseId-report-pdf-download-url`) —
  the full report download URL.

Download-URL endpoints expect `Accept: text/html` and return the URL itself rather than JSON.

## Beginning processing

If the case was created with customer-provided PII and not auto-processed, start it with
`PUT /case/id/{caseId}/action/beginprocessing` (`put-case-id-caseId-action-beginprocessing`).

**There is no un-begin.** Once processing starts, screenings are dispatched to external data sources
and fees are incurred.

## Placing a candidate

`PUT /case/id/{caseId}/action/place` (`put-case-id-caseId-action-place`) records that the candidate
meets the hiring criteria. A placed case remains cancellable unless another screening is added.

## Pre-adverse action — STOP AND ESCALATE

`POST /case/id/{caseId}/action/preadverse` (`post-case-id-caseId-action-preadverse`) initiates the
FCRA § 1681b(b)(3) pre-adverse-action procedure against a named individual.

**An agent must never call this autonomously.** It is:

- **irreversible** — no reversal operation exists;
- **a one-way door for the case** — once adverse action is initiated the case can no longer be
  cancelled;
- **a legal step with consequences for a real person's employment.**

Require explicit, recorded human approval. Retrieve the generated notice with
`GET /case/id/{caseId}/preadverse/{type}/pdf` and `.../pdf/download`.

## Archiving

`POST /case/archive/{caseId}` and `POST /case/unarchive/{caseId}` are a symmetric pair with no
documented expiry — **except** that archiving a case whose secondary status is `Waiting for
Authorization` or `Authorization in Progress`, or whose primary status is `Blocked`, **also cancels
it**, and unarchiving does not undo that cancellation. Check the status before archiving.
