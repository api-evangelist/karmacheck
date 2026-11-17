# KarmaCheck

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

KarmaCheck Inc. is a San Francisco based, API-first background check and credential verification company serving staffing, healthcare, gig-economy, call-center and IT/tech hiring workflows. The KarmaCheck API is a REST contract on api.karmacheck.io covering the full screening lifecycle: creating and placing cases, candidate onboarding with FCRA, e-signature, Canada, international and location-specific disclosure acknowledgement, criminal, identity, motor vehicle record, education, employment, professional-licence and occupational-health screenings, secure document upload and retrieval, package and service catalogs, jurisdiction lookup, verification-book search, adjudication and pre-adverse-action documents. Results are pushed asynchronously through Svix-delivered, HMAC-SHA256 signed webhooks (case.statuschange and casedata.statuschange). KarmaCheck also operates a remote MCP server so agents can order and track screenings from natural language, and integrates with Bullhorn, Workday and symplr CTM. The company holds a SOC 2 Type 2 report and operates as an FCRA consumer reporting agency.

**Areas:** Background Checks · Employment Screening · Identity Verification · Credential Verification · Motor Vehicle Records · Occupational Health Screening · Drug Screening · Human Resources · Staffing · Healthcare · Compliance · FCRA

## KarmaCheck on APIs.io

Everything profiled for KarmaCheck is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/karmacheck/](https://apis.io/providers/karmacheck/)** — or go straight to one of the APIs or properties below.

### APIs (9)

- [KarmaCheck Authentication API](https://apis.io/apis/karmacheck/karmacheck-authentication-api/) — The Authentication API from KarmaCheck — 1 operation(s) for authentication.
- [KarmaCheck Candidate onboarding API](https://apis.io/apis/karmacheck/karmacheck-candidate-onboarding-api/) — The Candidate onboarding API from KarmaCheck — 20 operation(s) for candidate onboarding.
- [KarmaCheck Case API](https://apis.io/apis/karmacheck/karmacheck-case-api/) — The Case API from KarmaCheck — 2 operation(s) for case.
- [KarmaCheck Cases API](https://apis.io/apis/karmacheck/karmacheck-cases-api/) — The Cases API from KarmaCheck — 22 operation(s) for cases.
- [KarmaCheck Packages API](https://apis.io/apis/karmacheck/karmacheck-packages-api/) — The Packages API from KarmaCheck — 4 operation(s) for packages.
- [KarmaCheck Secure documents API](https://apis.io/apis/karmacheck/karmacheck-secure-documents-api/) — The Secure documents API from KarmaCheck — 6 operation(s) for secure documents.
- [KarmaCheck Services API](https://apis.io/apis/karmacheck/karmacheck-services-api/) — The Services API from KarmaCheck — 5 operation(s) for services.
- [KarmaCheck Users API](https://apis.io/apis/karmacheck/karmacheck-users-api/) — The Users API from KarmaCheck — 1 operation(s) for users.
- [KarmaCheck Verification Book API](https://apis.io/apis/karmacheck/karmacheck-verification-book-api/) — The Verification Book API from KarmaCheck — 1 operation(s) for verification book.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Karmacheck Webhooks](https://apis.io/asyncapis/karmacheck/karmacheck-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [KarmaCheck MCP Server](https://apis.io/servers/karmacheck/karmacheck-mcp-server/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [KarmaCheck Agentic Access](https://apis.io/agentic-access/karmacheck/karmacheck-agentic-access/)

#### JSON Schema (26)

The data models the API reads and writes.

- [Authentication](https://apis.io/schemas/karmacheck/karmacheck-authentication/)
- [CaseData](https://apis.io/schemas/karmacheck/karmacheck-case-data/)
- [CaseOrderData](https://apis.io/schemas/karmacheck/karmacheck-case-order-data/)
- [CaseSummary](https://apis.io/schemas/karmacheck/karmacheck-case-summary/)
- [CPLC](https://apis.io/schemas/karmacheck/karmacheck-cplc/)
- [CPLCDefinition](https://apis.io/schemas/karmacheck/karmacheck-cplcdefinition/)
- [CreateCase](https://apis.io/schemas/karmacheck/karmacheck-create-case/)
- [DocumentCreateRecords](https://apis.io/schemas/karmacheck/karmacheck-document-create-records/)
- [DocumentFiles](https://apis.io/schemas/karmacheck/karmacheck-document-files/)
- [DocumentList](https://apis.io/schemas/karmacheck/karmacheck-document-list/)
- [DocumentRecords](https://apis.io/schemas/karmacheck/karmacheck-document-records/)
- [DocumentType](https://apis.io/schemas/karmacheck/karmacheck-document-type/)
- [LegalAcknowledgmentDisclosures](https://apis.io/schemas/karmacheck/karmacheck-legal-acknowledgment-disclosures/)
- [ListMetadata](https://apis.io/schemas/karmacheck/karmacheck-list-metadata/)
- [OrderConfig](https://apis.io/schemas/karmacheck/karmacheck-order-config/)
- [PublicVerificationBookItem](https://apis.io/schemas/karmacheck/karmacheck-public-verification-book-item/)
- [searchDetails](https://apis.io/schemas/karmacheck/karmacheck-search-details/)
- [ServiceGroupServices](https://apis.io/schemas/karmacheck/karmacheck-service-group-services/)
- [ServiceGroupServicesCase](https://apis.io/schemas/karmacheck/karmacheck-service-group-services-case/)
- [Testimony](https://apis.io/schemas/karmacheck/karmacheck-testimony/)
- [TestimonyAddress](https://apis.io/schemas/karmacheck/karmacheck-testimony-address/)
- [TestimonyDriversLicense](https://apis.io/schemas/karmacheck/karmacheck-testimony-drivers-license/)
- [TestimonyEducation](https://apis.io/schemas/karmacheck/karmacheck-testimony-education/)
- [TestimonyEmployment](https://apis.io/schemas/karmacheck/karmacheck-testimony-employment/)
- [User](https://apis.io/schemas/karmacheck/karmacheck-user-get-user-by-group/)
- …and 1 more published on APIs.io

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Karmacheck Context](https://apis.io/jsonld/karmacheck/karmacheck-context/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [KarmaCheck Api Overlay](https://apis.io/overlays/karmacheck/karmacheck-api-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [KarmaCheck API Rules](https://apis.io/rules/karmacheck/karmacheck-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [KarmaCheck Authentication](https://apis.io/security/karmacheck/karmacheck-authentication/)
- [KarmaCheck Domain Security](https://apis.io/security/karmacheck/karmacheck-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [KarmaCheck Plans Pricing](https://apis.io/plans/karmacheck/karmacheck-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [KarmaCheck Rate Limits](https://apis.io/rate-limits/karmacheck/karmacheck-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [KarmaCheck Finops](https://apis.io/finops/karmacheck/karmacheck-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.karmacheck.com/)
- [Documentation](https://developer.karmacheck.com/background-check-api/overview/introduction)
- [Getting started](https://developer.karmacheck.com/background-check-api/guides/candidate-provided-pii-flow)
- [API reference](https://developer.karmacheck.com/api-reference/authentication/authenticate-api-client)
- [Support](https://www.karmacheck.com/contact-us)
- [Blog](https://www.karmacheck.com/blogs)
- [Terms of service](https://www.karmacheck.com/tos)
- [Privacy policy](https://www.karmacheck.com/privacy-policy)

## API Evangelist rating

**Kin Score 49.3** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 61.0 |
| Contract governance | 18.2 |
| Operational transparency | 23.7 |
| Developer ergonomics | 66.1 |
| Access clarity | 35.5 |

**Agent readiness 54.1** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | verified |
| MCP Server | documented (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 23.4** — Health

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/karmacheck/](https://apis.io/providers/karmacheck/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for KarmaCheck: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/karmacheck/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
