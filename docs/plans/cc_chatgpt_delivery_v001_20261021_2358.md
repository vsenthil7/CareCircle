# CareCircle — delivery to market
21 October 2026 23:58 Europe/London · v001 · Proposal with assumptions.

## Status and sequence
Research and architecture proposal complete. Implementation, customer validation, live provider access, independent reviews, UAT and deployment remain unperformed.

| Sprint / deliverable | User outcome | Exit condition |
|---|---|---|
| S0 product/access contract | Agreed users, buyer experiment, boundaries and UAT | ADRs, threat model, acceptance IDs, model/API access, budget and license decision |
| S1 trusted circle | Recipient preferences, invitations, roles and revocation | Tenant isolation, two-session auth and lifecycle tests, real MCP profile |
| S2 central loop | Check-in → owned task → accepted handover | Accessible UI, restart/concurrency and core AC evidence |
| S3 scheduling/conflicts | Recurrence, rota gaps, changed appointments and exceptions | DST, cancellation/reassignment and conflicting-edit tests |
| S4 external actions | One live calendar and one notification path | Exact approvals, provider receipts, idempotency and uncertainty tests |
| S5 conversational assistance | Source-linked summaries, note-to-proposal, optional voice | Real authenticated inference, grounding/injection/cost/latency evidence; manual fallback |
| S6 release candidate | Onboarding, help, incident response, backups and runbook | Whole-sprint reviews, security/a11y/UAT and restore/rollback proof |
| S7 measured pilot | Consented recurring use against existing tools | Predeclared time/retention/burden/willingness-to-pay measures |
| S8 paid launch/learning | Reproducible release, support and spend monitoring | Launch decisions, SLOs, unit economics and continuing defect tracking |
| Later partner slices | Agency records, transport/pharmacy logistics, native Alexa | Actual API permissions, terms and runtime proof; new slice estimates |

Sprints are deliverables, not promised weeks. Each contains independently reviewable vertical slices. A synthetic demo is an early milestone within the full roadmap.

## Estimates and dependencies
Planning ranges, not commitments: synthetic core approximately 3–7 focused engineering days after scope/access agreement; live multi-user pilot readiness another 10–20; four weeks pilot observation; paid-release hardening another 5–15 days depending on findings. Some work may overlap. Access approval, privacy review and reviewer availability can dominate calendar duration.

Assumptions: one developer, hosted model, managed identity/database, two connectors, accessible web, sequential lightweight local runs and no clinical decisions. Ranges include testing/review but cannot predict defect rounds. Re-estimate S0 after a real provider call and connector sandbox checks. Larger agency suite/native apps require fresh estimates.

## Hackathon milestone
Rules/FAQ rechecked 21 October. Deadline unchanged: **23 October 2026 20:00 Europe/London**. Approximately 44 calendar hours remain from this page opening, not 44 engineering hours. Full paid-service delivery is not substantiated within that window.

A credible entry would show two authenticated roles completing one durable loop via real MCP, visible unaccepted work and a denied unauthorized action. Synthetic adapters must be labelled. Claims of live AI require actual model authentication/call evidence.

Native Alexa tooling remains restricted. The recommended profile is 2025-11-25 Streamable HTTP with a real web host/client. Rules also permit a separate simulated-experience path. Public submission needs deliberate open-source license selection, run instructions, functioning short demo and product feedback. No license or submission was completed here.

## Engineering baseline and loop
Proposed product baseline: standards commit 909db9574d46480159214c253c2f058cf4eed97c; build-loop v004, policy v004, DoR/DoD v002, rubric v002. Workbench remains pinned to f1c450a S2.9; this does not silently upgrade it.

Policy stages: smoke → ready → plan/threat-model → tests-first → build → applicable verification types → fix → test-change-review → internal-review → external-review → done → release → operate → learn. Slice defect-prevention Learn evidence is required before Done; whole-sprint reviews are additional.

Test/fixture/load/penetration/market scripts are committed/pushed before execution. Results name source commit, command, interpreter, environment, timing and actual outcome. Fixers do not weaken tests; test-bug/test-gap tracked separately. Each regression fails on its parent. Fix attempts bounded per policy. Internal review uses fresh context; external reviewer truly separate. No such review is claimed for this discussion.

## Test and release strategy
| Area | Required evidence |
|---|---|
| Domain/auth | Positive/negative/boundary per AC, concurrent sessions, revocation/version races |
| MCP | Real selected-profile client/server calls; invalid origin/version |
| Providers | Authorized sandbox contracts, failures, duplicates and receipt reconciliation |
| AI | Factuality/source IDs, injection, tenant leakage, unsafe requests, outage and cost caps |
| UX | Keyboard, screen reader, recipient comprehension, nonvoice fallback |
| Operations | Restart/scheduler, load baseline, restore/incident drills and minimal telemetry |
| Market | Time saved net of entry/approvals, repeated use and actual payment willingness |

Applicable gates: 100% changed-line/branch coverage, mutation >=80%, no new critical/high vulnerabilities, zero secrets, no unexplained weakened tests, no open P0/P1 and explicit P2 decisions. None of these product tests has run.

## Cost/access worksheet before deployment
The installation trial did not validate model credentials; prior AWS authentication failed. Installed SDKs do not prove native Alexa/provider permissions.

Budget database, app/worker, identity, email/SMS/voice, inference, logs/backups, support, payment fees and connector maintenance. Obtain dated regional unit prices/quotas before quoting spend.

Inference cost = active circles × calls per circle × (input tokens × input unit rate + output tokens × output unit rate), with matching units; cache/transcription/voice/retry categories separate. Track actual usage. Per-circle quotas, tool-step limits and daily spend caps are required. Credits are not a sustainable business model. No hosting/model price or margin is verified yet.

## Next decision
Approve or revise: **start with family care logistics that converts changed plans into named, accepted handovers, retaining agency-compatible boundaries**. S0 then makes domain/provider contracts and the first build slice concrete. Research/discussion does not authorize implementation/deployment.

## References
- [Market and sources](../research/cc_chatgpt_market_v001_20261021_2358.md)
- [Architecture and ACs](../architecture/cc_chatgpt_architecture_v001_20261021_2358.md)
- [MCP release](https://blog.modelcontextprotocol.io/posts/2026-07-28/)
- [Organizer FAQ](https://amazonappdev2026.devpost.com/details/faqs)
- [Rules](https://amazonappdev2026.devpost.com/rules)
