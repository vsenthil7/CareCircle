# CareCircle — current market and positioning
21 October 2026 23:58 Europe/London · v001 · Research, not validated demand.

## Recommendation
Continue with a **care-logistics coordinator that resolves changed plans into named, explicitly accepted handovers**. Treat this as a testable proposition. The original broad gap claim is unsupported: calendars, care plans, family updates, voice assistance and AI summaries already have competitors.

No competitor was tested signed in. Published features below are vendor/publisher statements, not independently observed runtime behaviour. An undocumented feature is not proof of absence.

## Comparison
| Alternative | Existing offer | Price / maturity observed | Implication |
|---|---|---|---|
| Caring Village [S01–02] | Family tasks/calendar/sharing; professional care coordination | Free/$14.99/$24.99 monthly; professional annual tiers from $499.99 | Generic family hub and agency portal already occupied |
| Jointly [S03] | Assigned tasks, calendar, notes and communication | £2.99 one-off circle | Strong low-cost substitute; subscription needs measurable extra value |
| Lotsa Helping Hands [S04] | Community requests, reminders and volunteer coordination | Opened My Cancer Circle offer free | Organizing helpers alone is insufficient |
| Birdie [S05] | Family visibility into agency-delivered care | Agency platform; price not verified | Avoid duplicate record entry; integrations require access |
| Wellthy / Cariloop [S06–07] | Digital tools and human coordination through employers | Covered benefit / commercial contract | Established buyers, distribution and competition |
| CaringIQ [S08] | Proactive text assistant, shared record, follow-ups | Advertised free beta | Familiar messaging plus AI already claimed |
| AyuraAI [S09] | Care coordination, AI summaries | Pre-launch / early access | AI elder-care summaries are not unique |
| Caily AI / Caily [S10–11] | Phone assistant pilot / senior-living communication | Different sites; prices/adoption unverified | Voice and family communication are contested |
| Existing messaging/calendar | Familiar current-tool baseline to measure with users | Migration effort effectively zero | Measure net work saved, including onboarding |

NAC/AARP [S12] supports a substantial care burden. It does not establish willingness to switch, retention, acquisition costs or CareCircle's addressable revenue.

## Initial user and buyer
Recommended user hypothesis: a family coordinator and at least two helpers handling recurring nonclinical logistics, with the recipient's preferences and authority explicitly represented. A paid helper may join under scoped delegation; family relationship alone grants no authority.

Competing buyer hypotheses: a family pays for less chasing; an independent coordinator/agency pays for fewer follow-ups. Agency deployment adds procurement, integration and duplicate-entry risks. Employer benefits are a later option. No single buyer or billing model is validated.

## Build, integrate or stop
| Decision | Recommendation |
|---|---|
| Build | Assignment acceptance, conflicting changes, exact proposal approvals, accepted handovers, overdue exceptions and provenance |
| Integrate | Managed identity, one calendar, one notification provider after actual API/account tests |
| Defer pending access | Pharmacy/transport transactions, agency-system integration and native Alexa publishing |
| Avoid claims | “Only AI care coordinator”, guaranteed safety, voice proves identity, notification proves care completion |
| Prefer an adapter | If incumbent workflow tests show the remaining pain is only moving data between systems |
| Stop/pivot | Current tools solve the same journey as easily; helpers do not acknowledge; approvals/dual entry cost more time than saved; no buyer commits |

## Validation plan — not executed
After agreement, prepare a consented learning pilot of approximately five circles and two professional coordinators. This is not a representative market sample. No outreach is authorized by this plan.

Compare the same rescheduled appointment journey in current tools and CareCircle: changed time → conflict → approved owner → helper acceptance → handover → reported closure. Measure coordinator minutes, reminders, unaccepted assignments, errors and recipient burden.

Proposed predeclared thresholds: 30% less coordinator handling time; 80% of eligible handovers accepted within the agreed deadline; no unauthorized action/disclosure in observed cases; three circles still using weekly after four weeks; two buyers accepting an explicit paid continuation offer. Targets are hypotheses to agree before measurement; disclose dropouts and small sample size.

Price remains undecided. Test family subscription versus agency per-active-circle fee/minimum plan. Competitor prices are anchors, not evidence for our pricing. Include support and integration maintenance in margins.

## Source register
Opened 21 October 2026 approximately 23:56–23:58 Europe/London. Search does not expose exact wall time per request. Retrieval date is not publication date. No user history used as market evidence.

### S01 — Caring Village pricing
[Primary page](https://caringvillage.com/pricing/)
Published offer: free tier; Circle $14.99/month; Village $24.99/month. Annual billing is separate. Calendar, tasks, sharing and care plans overlap with the proposal.

### S02 — Caring Village professionals
[Primary page](https://caringvillage.com/for-professionals/)
Published annual tiers $499.99/10 clients, $999.99/25, $1,499.99/50. Family/caregiver records and access controls. Vendor savings calculator is an estimate.

### S03 — Carers UK Jointly
[Primary page](https://www.carersuk.org/help-and-advice/technology-and-equipment/jointly-app-for-carers/)
Publisher documents assigned tasks, notes, calendars and communication. One-off £2.99 per circle; invited helpers have no additional charge.

### S04 — Lotsa Helping Hands
[Primary page](https://lotsahelpinghands.com/how-it-works)
Help requests, volunteers, reminders and shared updates. Opened page describes My Cancer Circle communities as free; do not generalize all related services' terms.

### S05 — Birdie workflow
[Primary page](https://www.birdie.care/blog/real-time-family-care-updates)
Vendor describes read-only family visibility into agency care and visit updates. Comparable price and open API access not established.

### S06 — Columbia Wellthy benefit
[Primary page](https://humanresources.columbia.edu/content/wellthy)
Customer/employer confirms covered digital tools plus human coordinators handling logistical and administrative work. Evidence of distribution, not CareCircle demand.

### S07 — Cariloop FAQ
[Primary page](https://cariloop.com/about-us/faqs)
Vendor describes employer caregiver support and care coaches; competes for coordination budgets. Public comparable contract price not established.

### S08 — CaringIQ
[Primary page](https://www.caringiq.com/)
Vendor claims text-based proactive caregiver assistant, shared record and follow-up reminders. Advertised free beta. No account/runtime/adoption tested.

### S09 — AyuraAI
[Primary page](https://www.ayuraai.co.uk/)
Vendor claims care coordination and human-checked AI summaries. Explicit pre-launch/early-access status, not established deployed capability.

### S10 — Caily AI
[Primary page](https://www.caily.ai/)
Vendor claims phone-accessible senior assistant and family updates; invites pilot participation. Runtime and adoption unverified.

### S11 — Caily
[Primary page](https://www.caily.com/)
Vendor claims senior-living communications platform. Compliance is a vendor assertion, not independently assessed. No corporate relationship with similarly named sites assumed.

### S12 — NAC/AARP research project
[Primary page](https://www.caregivingintheus.org/)
2025 study describes 63 million US caregivers. Burden evidence; not a UK market size or paying-user estimate.

### S13 — MCP release
[Primary page](https://blog.modelcontextprotocol.io/posts/2026-07-28/)
Official current release changes statefulness and interaction patterns; Tasks moves to an extension. Host/version compatibility needs explicit tests.

### S14 — MCP Streamable HTTP
[Primary page](https://modelcontextprotocol.io/specification/2026-07-28/basic/transports/streamable-http)
Official specification defines POST endpoint, headers, origin validation and backward-compatibility changes.

### S15 — MCP authorization
[Primary page](https://modelcontextprotocol.io/specification/2026-07-28/basic/authorization)
Official HTTP authorization model. Transport authorization does not replace circle/object permissions.

### S16 — Alexa+ MCP Toolkit
[Primary page](https://developer.amazon.com/docs/alexaplus/add-ons/mcp-toolkit-overview)
Official page specifies 2025-11-25 support with Alexa as client. Documentation availability is not an access entitlement.

### S17 — Organizer FAQ
[Primary page](https://amazonappdev2026.devpost.com/details/faqs)
Native tooling remains restricted; own real MCP web client accepted without physical Alexa hardware.

### S18 — Organizer rules
[Primary page](https://amazonappdev2026.devpost.com/rules)
Deadline 23 October 2026 noon Pacific = 20:00 Europe/London. Working source, instructions and demo required. Public entry needs open-source license. Separate simulation route permitted.


## Retrieval limitations and evidence labels
Jointly app root was JavaScript-only, so publisher documentation was used. AARP direct report page returned 403; official research-project site opened instead. Agency customer page returned 403 and was not treated as verified evidence. CaringIQ fetched successfully once; a repeat failed. No competitor purchase, live provider API, native Alexa entitlement or independent reliability trial occurred.

FACT: page text/displayed price/stage. VENDOR CLAIM: advertised functionality/results. INFERENCE: recommended positioning. HYPOTHESIS: unmet need, targets and willingness to pay. UNKNOWN: reliability, adoption and undocumented access.
