# Project Aether Environmental Assurance Architecture

**Status:** Implemented architecture through Project Aether Assurance V32 (Module 2 complete).

**Explorer baseline:** Project Aether V25 remains immutable. The live repository was inspected before implementation and V25 was confirmed as the highest published directory at the start of Module 1.

**Assurance implementation:** Module 1 was archived as V26–V29. Module 2 was archived as V30 property liability/land-close controls, V31 partner/study assurance, and V32 integrated Module 2. The current Assurance schema is version 3 with sequential migrations 1 → 2 → 3.

## Implementation Record — Module 1 Assurance Foundation

This section records the implemented architecture and supersedes version-number assumptions in the original planning sequence below. It does not change the future module missions in the modular roadmap.

| Archive version | Implemented boundary | Schema |
|---|---|---|
| V26 | Assurance-specific shell, executive summary, explicit prototype boundaries, responsive routes, keyboard focus, reduced motion, and print behavior | Shell only |
| V27 | `window.AetherAssurance`, normalized collections, stable IDs, independent condition/evidence/workflow axes, validation, decision precedence, and local demonstration history | 1 |
| V28 | Requirements/evidence register, filters, sorting, mobile cards, owner queue, record detail, controlled local edits, and reference protection | 1 |
| V29 | Decisions/escalations, schema 1 → 2 migration, structured local persistence, JSON import/export, local backup/reset, invalid-state quarantine, and internal self-tests | 2 |

### Implemented normalized collections

- `projects`
- `assuranceRecords`
- `evidenceReferences`
- `partners`
- `milestones`
- `studies`
- `liabilityControls`
- `decisions`
- `escalations`
- `localChangeHistory`
- `settings`

### Persistence contract

- Current state: `project-aether-assurance-v3`
- Legacy inputs: `project-aether-assurance-v2`, `project-aether-assurance-v1`
- Replaceable local backup: `project-aether-assurance-backup-v3`
- Recoverable invalid text: `project-aether-assurance-quarantine-v3`

The JSON export contains normalized workflow data and evidence metadata/references only. It is not secure document custody, authenticated authorship, immutable history, or enterprise multiuser recordkeeping.

### Integration boundary

Module 1 is intentionally self-contained. It establishes the shared internal namespace and record contracts without coupling to or modifying Explorer V25. A later integration module may exchange selected data through explicit versioned interfaces, but Explorer and Assurance remain independently loadable static applications.

### Validation limitations carried forward

Automated static checks and a mocked JavaScript runtime were available. A real browser automation launch was not reliable in the implementation environment, so physical mobile/touch behavior, screen-reader behavior, print pagination, browser file permissions, normal-origin storage persistence, and cross-browser runtime behavior remain manual.

## 1. Purpose

Project Aether already evaluates demand reduction, retrofit, site fit, grid, water, zoning, cost, community burden, lifecycle readiness, policy, evidence, and public accountability. The next architectural step is to connect these systems into an environmental assurance layer that can answer five questions consistently:

1. What requirement, commitment, risk, permit, or finding exists?
2. Who owns it and who is accountable for resolving it?
3. What evidence is required to establish its status?
4. What project decision, cost, schedule, or public commitment does it affect?
5. What happens when it is late, contradicted, expired, failed, or breached?

The goal is not to turn Aether into legal, engineering, or environmental-certification software. It remains a static screening and communication tool. The goal is to make execution risk, evidence quality, accountability, and decision consequences explicit enough that the conceptual framework behaves like a credible project-governance system.

## 2. Current-State Assessment

V25 already contains several useful foundations:

- Evidence-gated recommendations that distinguish verified, missing, and failed items.
- A lifecycle readiness matrix with named owners, evidence expectations, and blocking consequences.
- A dependency-aware permitting timeline.
- Community-commitment and claim-verification concepts.
- Role-specific views for developers, operators, planners, utilities, elected officials, and the public.
- Local browser persistence and internal self-tests.

The architectural gap is that these systems are largely generated from separate hard-coded arrays and individual controls. They describe governance, but they do not share one canonical record model. A permit condition, consultant deliverable, community commitment, construction finding, and environmental liability issue should all be able to flow through the same evidence, owner, deadline, consequence, and escalation logic.

The next implementation should therefore add one internal source of truth instead of adding more disconnected cards.

## 3. Architectural Principle: One Assurance Record, Multiple Views

Create a single internal namespace:

```js
window.AetherAssurance
```

It will own the environmental-assurance data, calculations, persistence, event dispatch, validation, and rendering helpers. Existing thermal, location, cost, policy, and impact models remain separate, but they publish relevant updates to the assurance engine.

The central model should support these record classes:

- **Standards** — corporate minimums, current legal requirements, permit criteria, lender or insurer requirements, and project-specific standards.
- **Obligations** — permit conditions, community commitments, lease terms, utility requirements, financing covenants, operating commitments, and reporting duties.
- **Evidence** — reports, letters, permits, inspections, test results, maps, contracts, approvals, monitoring data, and professional reviews.
- **Findings** — environmental conditions, study exceptions, compliance deficiencies, incidents, complaints, audit observations, and unresolved conflicts.
- **Actions** — mitigation, corrective action, additional investigation, redesign, agency coordination, contract revision, or stop-work response.
- **Partners** — consultant, developer, utility, EPC, contractor, commissioning authority, operator, regulator, community counterparty, insurer, or lender.
- **Milestones** — land option, land close, basis-of-design freeze, permit submission, procurement release, notice to proceed, energization, substantial completion, operational acceptance, expansion, or closure.
- **Decisions** — advance, investigate, redesign, renegotiate, pause irreversible spend, stop work, relocate, no-build, accept, reject, or close.

All visible modules should render filtered views of these shared records.

## 4. Status Architecture

Aether must not use one generic status field. Each record requires three independent status axes.

### 4.1 Condition state

Describes the real-world condition being evaluated:

```text
unknown
acceptable
conditional
failed
not_applicable
```

### 4.2 Evidence state

Describes whether the condition is supported by adequate evidence:

```text
missing
requested
received
under_review
verified
rejected
expired
disputed
```

### 4.3 Workflow state

Describes the work required to resolve or manage the record:

```text
not_started
open
in_progress
awaiting_third_party
awaiting_agency
ready_for_verification
closed
```

This prevents the project from treating a missing report as a confirmed failure or treating a submitted report as verified evidence.

## 5. Canonical Data Schema

The assurance state should use a schema version so future archived versions can migrate browser-saved data safely.

```js
const assuranceState = {
  schemaVersion: 1,
  projectId: "aether-demo-project",
  activeSiteId: "current-location",
  records: [],
  partners: [],
  milestones: [],
  decisions: [],
  settings: {
    demoMode: true,
    showInternalNotes: false,
    escalationProfile: "standard"
  }
};
```

### 5.1 Canonical assurance record

```js
{
  id: "ENV-LIAB-001",
  recordType: "finding",
  title: "Historic solvent use may require subsurface investigation",
  domain: "property_liability",
  phase: "pre_acquisition",
  jurisdiction: {
    country: "US",
    state: "WA",
    localAuthority: "screening only"
  },

  requirementType: "hard_gate",
  sourceClass: "screening_proxy",
  authority: "Professional environmental review required",

  conditionState: "unknown",
  evidenceState: "missing",
  workflowState: "open",

  severity: "high",
  confidence: "low",
  ownerId: "environmental-lead",
  accountablePartyId: "development-lead",
  reviewerId: "independent-reviewer",

  dueMilestoneId: "land-close",
  dependencies: ["PHASE-I-ESA", "TITLE-ACCESS"],
  affectedOutputs: ["verdict", "cost", "schedule", "site"],

  acceptanceCriteria: [
    "Phase I ESA completed by a qualified professional",
    "Recognized environmental conditions classified",
    "Phase II scope completed where recommended",
    "Liability allocation documented before land close"
  ],

  blockingConsequence: "Do not close on the property or represent the site as cleared",
  mitigationOptions: [
    "Additional investigation",
    "Seller remediation",
    "Price adjustment",
    "Indemnity and escrow",
    "Environmental insurance",
    "Reject or relocate"
  ],

  exposure: {
    scheduleDays: 90,
    costLow: 250000,
    costExpected: 1250000,
    costHigh: 10000000,
    publicRisk: "moderate",
    operationalRisk: "low"
  },

  escalationRuleId: "ESC-HIGH-PRELAND",
  evidenceRefs: [],
  actionIds: [],
  lastUpdated: "",
  notes: "",
  manualVerificationRequired: true
}
```

### 5.2 Evidence reference

Aether should store evidence metadata only. It should not pretend to securely store uploaded professional reports in a self-contained public HTML file.

```js
{
  id: "EVID-001",
  recordId: "ENV-LIAB-001",
  title: "Phase I Environmental Site Assessment",
  evidenceType: "professional_report",
  documentDate: "",
  receivedDate: "",
  reviewer: "",
  qualification: "",
  sourceUrl: "",
  localReference: "Document-control reference only",
  expiryDate: "",
  acceptanceState: "under_review",
  acceptanceNotes: "",
  supersedesEvidenceId: null
}
```

## 6. Decision Precedence

The Environmental Assurance Engine must preserve Aether's non-compensatory doctrine.

### 6.1 Precedence order

1. Confirmed failed hard gate
2. Critical evidence missing, rejected, disputed, or expired
3. Open critical corrective action or uncontained incident
4. Permit, commitment, or standard noncompliance
5. Schedule and cost exposure requiring executive decision
6. Comparative suitability
7. Optimization score

### 6.2 Decision states

```text
STOP / RELOCATE
PAUSE IRREVERSIBLE SPEND
REDESIGN OR RENEGOTIATE
DILIGENCE ONLY
CONDITIONAL ADVANCE
ADVANCE TO NEXT PROFESSIONAL GATE
OPERATE WITH MONITORING
CLOSE VERIFIED
```

A favorable PUE, WUE, carbon, cost, or design score must never override the first four categories.

## 7. UI Placement Without Expanding the Top Navigation

The existing top navigation is already dense. The new architecture should use the current routes rather than add another permanent top-level route.

### Decision + alternatives

Add an **Environmental Assurance Summary** immediately after the current verdict:

- Controlling assurance issue
- Open hard gates
- Critical evidence due
- Open high-severity findings
- Permit critical-path state
- Unmet or unverified commitments
- Current escalation action

This is the only place where the whole assurance system is summarized.

### Site + water

Add **Property and Environmental Liability**:

- Site-history and acquisition-risk screen
- Phase I / Phase II decision pathway
- Contamination and hazardous-material inventory
- Liability-allocation matrix
- Land-close conditions
- Remediation, indemnity, insurance, escrow, and reject-site options

### Systems

Add **Delivery Assurance**:

- Consultant and partner governance
- Study acceptance and independent review
- Permit and agency critical path
- Environmental management plans
- Construction inspection and compliance plan

### Accountability

Add **Commitments and Corrective Action**:

- Environmental commitments register
- Construction and operational findings
- Corrective and preventive action register
- Incident, complaint, and recurrence tracking
- Expansion and closeout gates
- Public versus internal reporting views

### Evidence

Add the **Evidence Control Register**:

- Evidence owner
- Document type
- Source date
- Reviewer
- acceptance criteria
- expiration or renewal date
- superseded status
- outputs affected by stale or rejected evidence

## 8. Module Architecture

## 8.1 Property Environmental Liability and Land-Close Gate

### Purpose

Determine whether environmental conditions, historical uses, hazardous materials, remediation duties, or contractual allocations make acquisition unacceptable, investigatory, negotiable, or manageable.

### Coverage

- Phase I ESA and recognized environmental conditions
- Phase II investigation triggers
- UST and AST history
- PFAS and emerging-contaminant screening
- PCBs, asbestos, lead, refrigerants, oils, batteries, and hazardous building materials
- Vapor intrusion
- Soil, groundwater, sediment, and surface-water concerns
- Brownfield or voluntary-cleanup status
- Existing permits, notices, violations, liens, or cleanup orders
- Access rights for investigation and remediation
- Seller representations, indemnities, escrow, insurance, and survival periods
- Remediation standards and intended-use compatibility
- Closure obligations and continuing controls

### Outputs

```text
CLEAR FOR PROFESSIONAL LAND-CLOSE REVIEW
ADDITIONAL INVESTIGATION REQUIRED
RENEGOTIATE RISK ALLOCATION
REMEDIATION PLAN REQUIRED
DO NOT CLOSE / RELOCATE
```

### Hard-gate rule

Land close remains blocked when a material recognized condition is unresolved, investigation access is unavailable, cleanup responsibility is unknown, or financial exposure cannot be bounded.

## 8.2 Consultant and Partner Governance

### Purpose

Evaluate whether the organizations producing evidence and delivering the project are qualified, independent, adequately scoped, and accountable.

### Partner record fields

- Organization and role
- Scope responsibility
- Named project manager
- Required qualifications and licenses
- Independence or conflict status
- Insurance and contractual requirements
- Deliverable schedule
- Data and file-format requirements
- QA/QC process
- Site-safety requirements
- Audit rights
- Corrective-action history
- Performance status

### Partner performance dimensions

- Technical completeness
- Schedule reliability
- Responsiveness
- Evidence traceability
- Conflict disclosure
- Field and construction safety
- Corrective-action closure
- Data usability

Critical failures are not averaged away. A consultant with a strong schedule score but an unacceptable technical or independence failure remains unacceptable for the affected decision.

## 8.3 Third-Party Study Audit and Acceptance

### Purpose

Prevent reports from becoming “verified” merely because they were submitted.

### Acceptance checklist

Every study should be reviewed for:

- Correct property and project boundary
- Qualified preparer
- Appropriate method and current standard
- Adequate seasonal and geographic coverage
- Complete assumptions and limitations
- Source data and chain of custody where applicable
- Internal consistency
- Conflict with other studies
- Clear findings and recommendations
- Defined uncertainty
- Actionable project consequences
- Required agency or professional acceptance
- Expiry or refresh date

### Acceptance states

```text
NOT RECEIVED
RECEIVED — NOT REVIEWED
ACCEPTED FOR SCREENING
ACCEPTED FOR CURRENT MILESTONE
REVISE AND RESUBMIT
REJECTED
SUPERSEDED
EXPIRED
```

“Accepted for screening” must not be treated as “accepted for land close,” “accepted for permit,” or “accepted for construction.”

## 8.4 Permit and Agency Critical Path

### Permit object

```js
{
  id: "PERMIT-001",
  title: "Construction stormwater authorization",
  authorityType: "regulatory",
  issuingBody: "Unverified local/state authority",
  applicabilityState: "research_required",
  phase: "preconstruction",
  dependencies: ["FINAL-GRADING-PLAN", "SWPPP", "OPERATOR-ID"],
  leadTime: { lowDays: 30, expectedDays: 60, highDays: 120 },
  publicProcess: false,
  seasonalConstraint: "",
  fieldWindow: "",
  appealRisk: "low",
  submissionState: "not_started",
  approvalState: "not_determined",
  conditionsImported: false,
  blocks: ["NOTICE-TO-PROCEED"]
}
```

### Critical-path functions

- Dependency validation and circular-dependency detection
- Earliest-start and earliest-finish calculation
- Low, expected, and high schedule range
- Agency pre-application milestone
- Public notice, hearing, consultation, and appeal windows
- Seasonal survey constraints
- Design-freeze dependencies
- Procurement-at-risk warning
- Land-control expiration warning
- Permit-condition import into the commitments register

### Visuals

Use an accessible dependency table as the source of truth. A compact SVG critical-path diagram may supplement it but must not be the only representation.

## 8.5 Construction Compliance, Findings, and CAPA

### Coverage

- Construction stormwater and erosion control
- SPCC and oil-management applicability screen
- Fueling, tanks, generators, and hazardous-material storage
- Spill prevention and response
- Dewatering and discharge
- Wetland, buffer, and protected-area controls
- Waste and hazardous-waste management
- Dust, air, noise, lighting, and traffic controls
- Concrete washout
- Contaminated-soil handling
- Worker and community complaint routing
- Environmental inspection frequency
- Permit posting and recordkeeping
- Subcontractor training
- Emergency contacts and agency notification
- Closeout documentation

### Finding severity

```text
OBSERVATION
MINOR
MAJOR
CRITICAL
```

### CAPA lifecycle

```text
IDENTIFIED
CONTAINED
ROOT CAUSE UNDER REVIEW
CORRECTIVE ACTION ASSIGNED
IMPLEMENTED
VERIFICATION PENDING
VERIFIED CLOSED
REOPENED
```

A finding cannot close solely because the action was marked complete. Closure requires an independent verification step appropriate to severity.

### Stop-work triggers

- Unpermitted discharge or impact
- Work outside approved limits
- Material spill without effective containment
- Repeated major finding
- Critical endangered-species, wetland, cultural-resource, or public-safety issue
- Falsified or missing required inspection records
- Agency stop-work or permit suspension

## 8.6 Environmental Commitments Register

### Sources

- Permit condition
- Development agreement
- Community-benefit agreement
- Utility agreement
- Lease or land agreement
- Financing or insurance covenant
- Public representation
- Corporate minimum standard
- Design basis
- Operational target

### Required fields

- Commitment text
- Source and evidence reference
- Beneficiary or protected resource
- Responsible party
- Accountable executive
- Start date, frequency, and end date
- Verification method
- Public or internal visibility
- Enforcement mechanism
- Consequence of breach
- Expansion relevance
- Status and latest evidence

### Rule

A proposed benefit is not a commitment. A commitment is not satisfied without evidence. A recurring commitment cannot remain “complete”; it must show the next due period.

## 8.7 Escalation Engine

The escalation engine converts assurance records into project action.

### Exposure dimensions

- Environmental severity
- Legal or permit exposure
- Schedule delay
- Cost exposure
- Operational reliability
- Community or reputational exposure
- Evidence integrity
- Recurrence

### Default escalation thresholds

**Red — automatic decision gate**

- Failed hard gate
- Critical environmental incident
- Permit denial, suspension, or material noncompliance
- Unacceptable land liability before close
- Critical study rejected
- Material public commitment breach
- Falsification or evidence-integrity issue

**Amber — executive review and pause on affected irreversible action**

- Major finding overdue
- Expected schedule delay greater than 30 days on a critical dependency
- Expected unbudgeted exposure greater than 5 percent of the relevant package
- Repeated minor or major finding
- Critical evidence expired or disputed
- Agency or community issue likely to alter project design or approval

**Yellow — action-owner review**

- Required evidence not requested by its planned date
- Deliverable more than 14 days late
- Acceptance criteria incomplete
- Commitment due within 30 days without current evidence

### Output

```text
CONTINUE
CONTINUE WITH CONTROLS
OWNER ACTION REQUIRED
EXECUTIVE REVIEW
PAUSE AFFECTED COMMITMENT
PAUSE IRREVERSIBLE SPEND
STOP WORK
RELOCATE / NO-BUILD REVIEW
```

## 8.8 Global Minimum Environmental Standards

### Purpose

Provide a jurisdiction-neutral floor without pretending to maintain a complete global legal database.

### Precedence

For each topic, the applicable requirement is the strictest verified combination of:

1. Current local law and permit conditions
2. Current national or regional law
3. Contractual, lender, insurer, or utility requirements
4. Project-specific commitments
5. Project Aether corporate minimum

When law is not verified, Aether must label it as research required. The corporate minimum may still be displayed as the internal screening floor.

### Standard domains

- Environmental and social due diligence
- Contaminated land and acquired-property liability
- Water availability, drought, treatment, discharge, and monitoring
- Biodiversity, wetlands, habitat, and ecosystem services
- Cultural heritage, tribal, Indigenous, and local-community engagement
- Air emissions, generators, refrigerants, and fuels
- Noise, traffic, lighting, and construction disturbance
- Hazardous materials, chemicals, batteries, oils, and waste
- Construction environmental management
- Climate resilience and natural hazards
- Energy, carbon, workload efficiency, and heat reuse
- Public-resource cost allocation
- Community commitments and grievance response
- Operational monitoring and disclosure
- Expansion, decommissioning, restoration, and financial assurance

### Global view

The interface should show:

- Corporate minimum
- Verified local requirement
- Which is stricter
- Evidence source and date
- Responsible reviewer
- Research gap
- Project action

It should not generate legal conclusions from country names alone.

## 9. Event and Integration Architecture

The assurance engine should subscribe to existing Aether events and publish its own.

### Existing events to consume

```text
aether:model-updated
aether:impact-updated
aether:location-change
```

### New events

```text
aether:assurance-updated
aether:evidence-changed
aether:finding-escalated
aether:milestone-blocked
aether:commitment-due
aether:decision-changed
```

### Example

When the shared project location changes:

1. Existing location models update.
2. Applicable assurance records are re-evaluated.
3. Jurisdiction-specific legal records return to `research_required` unless verified for the new location.
4. Site liability and permit assumptions are marked stale.
5. The executive verdict receives any new missing-evidence or failed-gate condition.

## 10. Persistence and Import/Export

### Local storage

Use a new schema-versioned key:

```text
project-aether-assurance-v1
```

Do not append hundreds of new form control IDs to the existing flat persistence list. Save the normalized assurance state as structured JSON.

### Migration

On load:

1. Read schema version.
2. Apply migrations sequentially.
3. Validate required fields.
4. Quarantine invalid records rather than silently discarding them.
5. Display a recovery warning if state cannot be migrated.

### Export

Provide:

- JSON project-state export
- Human-readable assurance report
- Commitments register CSV
- Findings and CAPA CSV
- Permit critical-path CSV
- Evidence-control CSV

Import should be optional and must validate schema, lengths, enumerations, and unsafe text before rendering.

## 11. Reusable Interface Components

Implement reusable renderers rather than module-specific one-off HTML.

- `renderAssuranceSummary()`
- `renderRecordTable(records, columns)`
- `renderEvidenceState(record)`
- `renderConditionState(record)`
- `renderWorkflowState(record)`
- `renderOwnerQueue()`
- `renderDependencyTimeline()`
- `renderCommitmentRegister()`
- `renderFindingCards()`
- `renderPartnerScorecard()`
- `renderStandardPrecedence()`
- `renderEscalationBanner()`

Each table requires a card-mode mobile alternative or responsive row transformation. Avoid adding more nested scrolling regions.

## 12. Calculation and Validation Functions

```js
AetherAssurance.evaluateRecord(record)
AetherAssurance.evaluateEligibility()
AetherAssurance.evaluateEscalation()
AetherAssurance.evaluateMilestone(milestoneId)
AetherAssurance.calculateCriticalPath()
AetherAssurance.validateEvidence(evidence)
AetherAssurance.validateStudyAcceptance(record)
AetherAssurance.canCloseFinding(findingId)
AetherAssurance.canAdvanceMilestone(milestoneId)
AetherAssurance.getApplicableStandard(domain)
AetherAssurance.getAffectedOutputs(recordId)
AetherAssurance.buildDecisionMemo()
```

All calculations must return explicit states and explanatory reasons, not only numeric scores.

## 13. Original Concept Sequence — Superseded by the Modular Archive

This was the original concept sequence before the modular roadmap assigned actual archive revisions. It is retained only as design history. The live implementation uses V26–V29 for Module 1 and V30–V32 for Module 2. Future sessions must inspect the live repository and follow the active modular roadmap; the concept-slice labels below are not version assignments.

### Concept slice A — Environmental Assurance Core

- Canonical assurance data model
- Three-axis status system
- Executive assurance summary
- Structured persistence and migration
- Event integration
- Basic evidence register
- New self-tests

### Concept slice B — Property Liability and Professional Assurance

- Acquired-property environmental liability
- Phase I / Phase II pathway
- Hazardous-material and contamination screen
- Consultant and partner governance
- Study audit and acceptance criteria

### Concept slice C — Permit and Commitments Architecture

- Permit and agency critical path
- Dependency and schedule-range engine
- Environmental commitments register
- Permit-condition import
- Milestone-blocking logic

### Concept slice D — Construction Compliance and Escalation

- Construction environmental management plan
- SPCC and hazardous-material applicability screens
- Inspection register
- Findings, incidents, complaints, and CAPA
- Stop-work and escalation engine
- Closeout package

### Concept slice E — Global Minimum Standards and Portfolio Readiness

- Global minimum environmental standards
- Local-versus-corporate precedence view
- Multi-site or multi-path comparison
- Portfolio escalation summary
- Presentation-oriented assurance route
- Final broad regression and professional-polish pass

These should remain separate archived versions because each is a substantive new operating system.

## 14. Acceptance Tests

### Data and decision logic

- Missing evidence never becomes a confirmed failure automatically.
- Received evidence never becomes verified without acceptance.
- Expired evidence reopens affected decisions.
- A failed hard gate withholds favorable composite scores.
- Critical finding closure requires verification.
- A recurring commitment shows the next due period.
- Permit dependencies cannot form a silent circular path.
- A blocked milestone prevents downstream “ready” status.
- A stricter verified local requirement overrides the corporate minimum.
- Unverified legal applicability remains labeled research required.
- Location changes invalidate location-dependent legal and permit assumptions.

### Accessibility

- Every control has a label and programmatic description.
- All tabs use correct keyboard behavior.
- Status is not communicated by color alone.
- Tables have accessible headers and mobile alternatives.
- Escalations use live regions without excessive announcements.
- Reduced-motion mode disables animated schedule or flow effects.
- Print output preserves record titles, states, owners, and consequences.

### Runtime and regression

- No duplicate IDs.
- All buttons have explicit types.
- No nonfinite numeric outputs.
- No horizontal page overflow at desktop or mobile widths.
- Saved-state migration succeeds from a clean and populated state.
- JSON import rejects malformed or unsupported schemas.
- Existing thermal, cost, location, policy, AI, lifecycle, and public-score systems still function.
- Presentation and Show All modes remain usable.

## 15. Manual Validation Still Required

- Professional environmental and legal review of terminology and decision criteria
- Current permit and regulatory applicability by jurisdiction
- SPCC, hazardous-material, waste, air, water, wetlands, cultural-resource, and construction requirements
- Contract, insurance, indemnity, escrow, and acquired-liability strategy
- Consultant qualification and professional-standard requirements
- Real agency sequence, review duration, field seasons, public process, and appeal risk
- Real construction inspection and stop-work authority
- Community and Indigenous engagement design
- Physical mobile and touch behavior
- Screen-reader behavior
- Browser print pagination
- Normal-origin browser storage and file-import behavior

## 16. Implementation Rule

The implementation must remain transparent about what the tool can and cannot establish:

- It may organize and screen environmental assurance work.
- It may identify missing evidence, conflicts, dependencies, exposure, and decision consequences.
- It may model example standards and workflows.
- It may not declare legal compliance, professional adequacy, permit applicability, property clearance, community consent, or engineering acceptance without verified external evidence and qualified review.

The environmental assurance architecture strengthens Project Aether because it turns its existing doctrine into an execution system: every claim has evidence, every requirement has an owner, every unresolved issue has a consequence, and every major decision preserves the ability to redesign, renegotiate, pause, or stop before risk becomes irreversible.

## Module 2 implementation record — Property Liability and Professional Assurance

### V30 — Property liability and land-close gate

- Added canonical property assurance records for Phase I/II, professional-review-dependent REC/CREC/HREC terminology, data gaps, hazardous building materials, PFAS, vapor, investigation access, continuing controls, and liability allocation.
- Added normalized `studies` and `liabilityControls` collections.
- Added land-close states: reversible diligence, conditional readiness, pause land close, and reject/relocate review.
- A failed property hard gate, material unresolved property condition, unaccepted critical study, or missing critical liability allocation controls land close before scores.
- Advanced schema to 3 with sequential migration 1 → 2 → 3.

### V31 — Partner governance and study acceptance

- Expanded partner metadata for role, discipline, qualifications/licenses, independence, conflicts, insurance, scope, schedule commitments, deliverables, assumptions/exclusions, QA/QC, reviewer authority, audit/access rights, subconsultants, performance, corrective action, and replacement/escalation pathways.
- Added third-party study statuses from receipt through milestone-specific acceptance, revise/resubmit, rejection, supersession, expiry, and dispute.
- Each acceptance requires a milestone, reviewer, criteria, limitations, date, and evidence reference. Receipt never implies verification or acceptance.

### V32 — Integrated Module 2

- Synchronized summary, property, professional, register, decision, persistence, and recovery views from normalized collections.
- Added deterministic tests for property precedence, milestone-limited acceptance, disputed/superseded studies, partner evidence gaps, liability allocation, migrations, stable references, malformed input, and nonfinite values.

## Current Assurance schema

- Schema version: **3**
- Migration chain: **1 → 2 → 3**
- State key: `project-aether-assurance-v3`
- Legacy keys: `project-aether-assurance-v2`, `project-aether-assurance-v1`
- Backup key: `project-aether-assurance-backup-v3`
- Quarantine key: `project-aether-assurance-quarantine-v3`

## Module 2 limitations

Evidence remains metadata/reference only. No screen or state claims secure document custody, authenticated authorship, tamper-proof history, legal compliance, environmental clearance, professional approval, insurance sufficiency, agency acceptance, community consent, or enterprise multiuser recordkeeping.
