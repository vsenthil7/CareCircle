# CareCircle — proposed architecture
21 October 2026 23:58 Europe/London · v001 · Proposed, not implemented or approved.

## Product behaviour
A circle reports a logistical change; CareCircle exposes conflicts, proposes a named owner, obtains approval on exact details, gets the helper's acceptance, and records an accepted handover.

Example: an appointment moves from 10:00 to 14:00. A ride assignment becomes invalid. A coordinator approves a new proposal and a helper accepts. A calendar entry is not a transport booking; a notification is not acknowledgement; a reported completion is not independently verified care.

Full roadmap: accessible onboarding, delegation, schedules/rota, recurring tasks, conflicts, check-ins, handovers, notifications, approved provider actions, oversight and operations. First slice proves the core loop, not commercial completion. No diagnosis, medication changes, inferred adherence or guaranteed emergency response.

## Components and boundaries
| Component | Responsibility and reason |
|---|---|
| Accessible React/TypeScript client | Today, needs-owner, conflicts, approval, handover and history; keyboard/text first, voice optional |
| Server-side host/BFF | Web session, model orchestration and real MCP client; provider secrets remain server-side |
| MCP adapter | Narrow schema-validated tools, explicit version/capability negotiation and request authorization |
| Domain service | Deterministic membership, delegation, policy and revision/state transitions; model suggests but never authorizes |
| Relational store + outbox | Transactional cases/tasks/proposals/events and delivery intents |
| Durable worker | Due work, overdue exceptions, bounded delivery and receipt reconciliation across browser/server restarts |
| Scoped provider adapters | Calendar and notifications first; additional services after access proof |
| Model adapter | Extract proposed changes, draft summaries with source IDs; output is untrusted |

Use a modular monolith plus worker initially. Microservices add deployment and consistency costs before boundaries/load justify them. Modules allow later separation.

## Stack and deployment decisions
TypeScript across UI/API/MCP reduces contract duplication. Reuse earlier installation findings only after version/dependency checks and lockfiles; they are prerequisite evidence.

SQLite suits synthetic single-process local development. PostgreSQL is proposed for a shared service because of concurrency and operational tooling. Never place a local database on ephemeral serverless storage. Migrations and real concurrent-session tests belong in the product repository.

Use managed OIDC identity rather than custom passwords. Identity vendor, region, host and model provider remain open. An AWS container app plus managed database/worker is possible; Lambda is another option, but neither supplies durability by itself. No deployment or paid resource is approved.

## MCP compatibility
Official current release is **2026-07-28**: stateless core, protocol/routing headers, Tasks extension and changed interactions [market S13–15]. Alexa+ documentation still specifies **2025-11-25** support [S16]. Organizer's real-client example uses initialize/list/call [S17].

Proposed initial profile: **explicit 2025-11-25 Streamable HTTP compatibility**, using real SDK client/server and captured initialization/list/call evidence. Durable business jobs are independent of optional protocol Tasks. Add July-profile support only after matching SDK/client contract tests; never mix older sessions/task semantics with the new core.

Native Alexa tools remain gated. Web client plus own MCP server is the verified permitted route; no native integration claim. Ordinary UI actions may use the same domain API, but a demo claiming MCP must actually invoke it.

## Domain contracts
| Entity | Invariant |
|---|---|
| Circle/Membership | tenant, actor, recipient, role, active/revoked and membership version; query-level object isolation |
| Delegation | grantor/grantee, action/resource scope, expiry/revocation; kinship is not authority |
| Task/Schedule | named owner, UTC instant plus IANA timezone, recurrence and revision; offer is not acceptance |
| Proposal/Approval | exact actor/action/recipient/content/time/expected revision/expiry digest; changed details invalidate approval |
| Handover | outgoing/incoming actor, referenced tasks, requested and accepted versions/timestamps |
| ActionAttempt/Receipt | unique idempotency key, provider reference, dispatch/confirmation/unknown state |
| Event/Outbox | actor, revision, correlation ID and minimal provenance; enqueue in same state-change transaction |

Task lifecycle: proposed → offered → accepted → in_progress → completion_reported → closed. Declined, cancelled and overdue remain explicit.

External action lifecycle: draft → approved → claimed → dispatched → provider_confirmed. Timeout after send can produce outcome_unknown, requiring reconciliation. Provider confirmation, recipient acceptance and care completion are distinct.

## Commands and authority
Initial tools: get_today, list_unowned_tasks, propose_assignment, approve_proposal, accept_assignment, request_handover, accept_handover, report_completion.

Actor identity comes from authenticated context, never an LLM-supplied actor ID. Filter storage queries and outputs by circle/object permission. Tool-list filtering is convenience, not authorization.

Approval binds exact proposal digest and expected object revision. Recheck delegation immediately before a transactional conditional claim, then external action. Unique idempotency key protects replay; two competing clients yield one winner and a clear conflict.

Revocation before dispatch blocks action. Revocation after an external write cannot erase it: display receipt, block future actions and propose a separately approved correction if supported.

## Failure, model and data handling
Retry reads/proven-idempotent internal work with bounds. Consequential external uncertainty gets no blind retry: reconcile using provider reference, then obtain authorization where required. Failures have visible owners and next steps.

Test crashes before send, after send/before receipt, duplicates, expired tokens, offline UI, concurrent edits, revoked delegates, rate limits, model outage and DST. Store UTC plus intended timezone/local schedule; define recurrence behaviour for DST before coding.

Send minimal authorized case content to the model. Notes/attachments/provider responses are untrusted input. Model has no SQL, secrets or unrestricted send tool. Summaries cite source event IDs and flag conflicting/stale facts. Bound tokens, tool steps, time and spend. Core workflow remains usable without model/voice.

Before real-data pilot, resolve jurisdiction, controller/processor roles, processing basis/conditions, recipient rights, retention/export/deletion, subprocessors, hosting and inference retention/training settings through appropriate review. These are launch decisions, not legal-compliance claims.

Keep health content/tokens/raw prompts out of general telemetry. Notifications default to minimal content and authenticated links. Encrypt in transit/at rest, isolate tenants, audit access and prove restore. Deletion must account for summaries/search data and documented backup expiry, retaining only justified audit metadata.

## Acceptance criteria — proposed
| ID | Given / when / then | Required evidence |
|---|---|---|
| AC01 | A member requests another circle's task / deny without leaking data | API and real MCP negative auth tests |
| AC02 | Two helpers accept same task concurrently / one valid owner | Two real sessions plus database assertions |
| AC03 | Approved recipient/time/content changes / reject until reapproved | Contract/mutation tests |
| AC04 | Delegation revoked before dispatch / no external write | Race test and adapter observations |
| AC05 | Worker restarts with overdue handover / preserve pending work | Restart/resilience scenario |
| AC06 | Provider accepts then times out / show unknown and prevent blind duplicate | Fault injection and reconciliation |
| AC07 | Notification delivered, helper silent / remain unaccepted | E2E state assertions |
| AC08 | Note requests cross-circle leakage / refuse without disclosure | Prompt-injection evaluation and authorization tests |
| AC09 | Model/voice fails / accessible manual loop works | Keyboard/screen-reader UAT and outage test |
| AC10 | Real client uses chosen MCP profile / correct list/call and invalid version/origin handling | HTTP contract evidence |
| AC11 | Summary asserts completion / link visible source or mark uncertain | Grounding eval fixtures/human rubric |
| AC12 | Authorized export/delete requested / match documented lifecycle | Integration tests |

## Proposed quality targets and open decisions
Initial performance scenario: 100 active circles and 10 concurrent coordinators; deterministic API p95 <500 ms, errors <1%, regression <=10% against comparable baseline. Measure inference separately; enqueue latency is not completion latency.

Proposed early paid-pilot targets: 99.5% monthly availability, RPO 24h, RTO 4h, subject to budget/restore proof. Provider acceptance and helper acknowledgement get separate metrics.

Use current policy's changed-code 100% line/branch and >=80% mutation gates plus security/dependency/contract/a11y/resilience/performance/penetration/market evidence where applicable. Coverage is no guarantee of correctness or market fit.

Open: first buyer, accepted-handover promise, provider/credentials, connector, region, budget, compatibility profile and license. No implementation, independent review or application test has occurred.
