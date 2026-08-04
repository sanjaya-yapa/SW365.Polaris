# Example 1.6 - Asking Better Questions

## Prompt

Project Polaris – Initial Business Request

A government agency wants to create an online grants management
portal for community organisations.

The portal should allow organisations to apply for grants and
track their applications.

Internal staff must be able to review and process applications.

## Response

## Discovery Approach for Project Polaris

The initial request is a useful starting point, but it is too broad to move directly into solution design. The first step should be structured discovery to clarify the business goals, grant rules, applicant needs, internal assessment process, and public-sector constraints.

### Business objectives that must be clarified
- Improve how community organisations apply for grants
- Give applicants visibility of application progress and status
- Enable staff to review and process applications efficiently
- Reduce manual effort, duplication, and delays
- Improve consistency, traceability, and accountability in decisions
- Ensure the service is secure, accessible, and compliant

### Likely stakeholder groups
- Community organisations and applicant representatives
- Grant program managers and business owners
- Assessment officers and reviewers
- Approval delegates and decision-makers
- Finance and compliance teams
- Privacy, security, and records management stakeholders
- Accessibility and digital inclusion stakeholders
- Support and operations teams
- Executive sponsors

### Questions for the first discovery workshop

#### Business objectives
- What business problem is the agency trying to solve?
- What outcomes define success for applicants, staff, and program owners?
- What pain points exist in the current process?
- Are there service targets or policy drivers behind this request?

Open questions:
- What current process issues are most severe?
- Which outcomes matter most: speed, consistency, transparency, or compliance?
- Are there mandatory policy or legislative requirements?

#### Applicant eligibility
- Who is eligible to apply?
- Are only community organisations included, or other entity types as well?
- Do eligibility rules vary by grant program?
- What evidence is required to prove eligibility?

Open questions:
- Is there one common eligibility model or several?
- How are ineligible applications handled?
- Can applicants save progress before submission?

#### Grant programs
- Will the portal support one grant program or multiple?
- Do different programs have different forms, rules, and timelines?
- Are grants open continuously or delivered in funding rounds?
- How often do program rules change?

Open questions:
- How many programs are in scope initially?
- Which rules are shared across programs?
- How are program changes managed?

#### Application processing
- What stages does an application go through?
- What information and supporting documents are required?
- Can applicants edit, withdraw, or resubmit applications?
- What statuses should applicants be able to see?

Open questions:
- What is the full lifecycle from draft to final outcome?
- What is mandatory at each stage?
- Are amendments allowed after submission?

#### Assessment and approval
- How are applications allocated to staff?
- Is there one reviewer or multiple reviewers?
- Are there scoring models, recommendation steps, or approval thresholds?
- What approval steps are required before a decision is final?

Open questions:
- Are assessment rules standard across programs?
- What exceptions or escalations must be supported?
- Is separation of duties required?

#### Document management
- What documents must applicants submit?
- What internal documents are created during assessment?
- Are templates, versioning, or retention rules required?
- Are there restrictions on file size, type, or volume?

Open questions:
- Which documents are mandatory by program or stage?
- What retention and archival obligations apply?
- Are staff-only documents or notes required?

#### Security and privacy
- What personal or sensitive information will be collected?
- What identity and access controls are needed for applicants and staff?
- What privacy obligations apply?
- What audit trail is required?

Open questions:
- What data classifications apply?
- What role-based access model is required?
- Which user and system actions must be auditable?

#### Reporting
- What operational, compliance, and management reporting is needed?
- What information must be visible to staff and leadership?
- Are dashboards, exports, or scheduled reports needed?
- Are external transparency or audit reports required?

Open questions:
- Which reports are mandatory?
- Who needs access to which reports?
- How much historical reporting is required?

#### Accessibility
- What accessibility standards must the portal meet?
- Are there known barriers in the current process?
- Are plain language or multilingual needs in scope?
- Are assisted submission scenarios needed?

Open questions:
- What accessibility compliance level is required?
- Are alternative submission channels needed?
- What support is needed for low digital literacy users?

#### Support and operations
- Who will support applicants and staff?
- What operational processes are needed to manage the portal?
- How will incidents, issues, and business changes be handled?
- Who owns ongoing administration?

Open questions:
- Which team owns day-to-day operations?
- What are the support hours and escalation paths?
- How are program changes introduced between funding rounds?

### Assumptions contained in the initial request
- Community organisations are the main applicant type
- Applicants are expected to use online self-service
- Tracking application status is a core user need
- Internal staff follow a defined review and processing workflow
- One portal will support both external applicants and internal staff
- The existing grant process can be digitised without major redesign

### Risks created by missing information
- Requirements may be based on incorrect assumptions
- Different grant programs may need very different workflows
- Review and approval complexity may be underestimated
- Privacy, audit, and records obligations may be missed
- Accessibility and usability needs may be overlooked
- Reporting and compliance requirements may emerge too late
- Operational ownership and support responsibilities may be unclear
- Solution design may begin before the business process is understood

### Functional and non-functional areas that require investigation

#### Functional areas
- Applicant registration and access
- Organisation profile management
- Grant discovery and eligibility checking
- Application creation, saving, editing, and submission
- Attachment and evidence handling
- Application tracking and notifications
- Staff review, assessment, and recommendation
- Approval and decision workflows
- Audit history and internal notes
- Reporting and administration

#### Non-functional areas
- Security and privacy
- Accessibility and inclusive design
- Auditability and records retention
- Performance and scalability
- Availability and reliability
- Usability and content clarity
- Supportability and operational administration
- Data quality and integrity
- Compliance obligations

### Recommended discovery outputs
- Business objectives and success measures
- Stakeholder map
- Discovery workshop question set
- Assumptions log
- Risks and issues log
- Current-state and future-state process views
- Scope boundaries and out-of-scope items
- Functional and non-functional requirement themes
- Prioritised areas for further requirements work

### Summary
This request is appropriate for a discovery phase, not for technical design yet. The immediate priority is to clarify grant program rules, applicant eligibility, assessment workflows, reporting obligations, accessibility expectations, and operational ownership so that later requirements are based on confirmed business needs rather than assumptions.