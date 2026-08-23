---
name: karmacheck-order-background-check
description: >-
  Order a KarmaCheck background check on a candidate using the candidate-provided PII flow, where
  the candidate supplies their own personal information through an emailed invitation. Use this when
  you have a candidate's name and email but not their SSN, date of birth or address.
api: KarmaCheck API
generated: '2026-08-23'
method: generated
source: >-
  openapi/karmacheck-api-openapi.yml +
  https://developer.karmacheck.com/background-check-api/guides/candidate-provided-pii-flow
operations:
  - post-auth-api
  - get-package-min-list
  - post-case-create
  - get-invitation-case-caseId
  - post-case-id-caseId-action-resendinvite
  - put-case-id-caseId-action-refreshinvite
  - get-case-id-caseid
  - get-case-id-caseId-services
  - post-case-id-caseId-cancel
---

# Order a background check (candidate-provided PII)

## Before you start — this is a regulated, billable, non-idempotent write

Creating a case orders a **consumer report under the US Fair Credit Reporting Act** on a named
person and emails that person an invitation. It costs money, including third-party passthrough fees
KarmaCheck does not set and does not publish. There is **no idempotency key**. Get explicit human
approval before calling `POST /case/create` in production, and confirm which base URL you are on:

| Environment | Base URL | Dashboard |
|---|---|---|
| Staging (sandbox) | `https://api-stage.karmacheck.io` | `https://app-stage.karmacheck.com` |
| Production | `https://api.karmacheck.io` | `https://app.karmacheck.com` |

Credentials carry **no test/live prefix**. The host is the only thing that tells you which world you
are in.

## 1. Authenticate

`POST /auth/api` (`post-auth-api`) with your `apiKey` and `clientAccessToken`. Read `token` from the
response and send it as `Authorization: Bearer <token>` on every later call. Never put it in a query
string.

The token **does not expire**, and it is scoped to **one group** within one company. If you get a
`403` on a case that you know exists, you are almost certainly holding the wrong group's token.

## 2. Choose a package

`GET /package/min/list` (`get-package-min-list`) returns the packages your group can order.
`GET /package/id/{packageId}/services` shows what a package contains. A case is always ordered
against exactly one `packageId`.

## 3. Create the case

`POST /case/create` (`post-case-create`) with the candidate's **first name, last name and email**
plus the `packageId`. Leave the PII fields out — omitting them is what selects the
candidate-provided flow.

The case comes back with status **Pending / Waiting for Authorization** and KarmaCheck emails the
candidate an invitation.

**Handle `409` before you retry anything.** Candidate email is the uniqueness key within a group. A
`409` returns `{ httpStatus, cases[] }` — a different envelope from every other error — listing the
existing cases. Adopt the existing case; do not order a second one.

**Never blind-retry a `500` on this call.** Without an idempotency key, a retry after a 500 that
actually succeeded either orders a second report or returns 409. Reconcile with `GET /case/list`
first.

## 4. Chase the invitation if the candidate stalls

- `GET /invitation/case/{caseId}` (`get-invitation-case-caseId`) — check invitation status.
- `POST /case/id/{caseId}/action/resendinvite` (`post-case-id-caseId-action-resendinvite`) — resend.
- `PUT /case/id/{caseId}/action/refreshinvite` (`put-case-id-caseId-action-refreshinvite`) — refresh
  an expired invitation.

## 5. Track the case

Prefer webhooks over polling. Subscribe to `case.statuschange` and `casedata.statuschange`, verify
the HMAC-SHA256 `webhook-signature` against the **raw** body, and treat every event as a signal to
re-fetch rather than as state:

- `GET /case/id/{caseId}` (`get-case-id-caseid`) — the case and its status.
- `GET /case/id/{caseId}/services` (`get-case-id-caseId-services`) — per-screening progress.

Events are **not ordered** and **may duplicate**. De-duplicate on case `id` plus `caseStatusId`,
`secondaryCaseStatusId` and `modStamp`. Acknowledge with a `2xx` within **15 seconds** — anything
else, including a `3xx`, counts as a failed delivery and starts an 8-attempt retry ladder.

If you must poll instead, note that `GET /case/list` **does not paginate**.

## 6. Cancelling

`POST /case/id/{caseId}/cancel` (`post-case-id-caseId-cancel`) reverses the order, but the window is
bounded by case **state**, not by a clock:

- Cancellable while **Pending**.
- At **Complete / Consider**: cancellable *unless* adverse action has been initiated or another
  screening has been added.
- At **Placed**: cancellable *unless* another screening has been added.
- Once **Canceled**: not reopenable without asking KarmaCheck.

Cancelling is not documented to refund passthrough fees already incurred at the data source.

## Errors you will actually hit

| Status | Meaning | What to do |
|---|---|---|
| 400 | Malformed payload | `message` is an array of dotted field paths. Fix and resend. |
| 403 | Wrong group, or `karmacheck-on-behalf-of` names a user without package access | Use the right group's token. |
| 404 | Bad ID — **may return bare text, not JSON** | Do not retry. |
| 409 | Duplicate candidate email in group — **different envelope** | Adopt `cases[]`. |
| 422 | Business-rule failure (case state forbids the action) | Do not retry unchanged. |
| 500 | KarmaCheck-side | Retry reads; reconcile before retrying writes. |

There is **no 429 and no published rate limit**, so there is no header to back off against.
