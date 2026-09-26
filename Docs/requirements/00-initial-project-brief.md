# Project Polaris – Initial Project Brief

## Document Status

**Status:** Initial Project Brief
**Purpose:** Provide sufficient project context for early analysis and AI-assisted demonstrations.
**Note:** This document does not represent the final approved requirements. Formal discovery and requirements engineering will be completed later in the project.

## Project Overview

Project Polaris is a Community Grants Management solution for a government agency responsible for providing funding to eligible community organisations.

The existing grants process relies heavily on email, documents, spreadsheets, shared folders, and manual communication. This makes it difficult for applicants to track applications and for internal staff to consistently assess, approve, and report on grant applications.

The proposed solution will use Microsoft Power Pages as the external-facing portal and Microsoft Dataverse as the primary business data platform.

Internal staff will use a model-driven application to manage grant programs and process applications.

Power Automate will support notifications, assignments, approvals, reminders, and other business-process automation.

## Initial Business Objectives

The proposed solution should:

* Provide community organisations with a secure online grants portal.
* Make available grant opportunities easier to discover.
* Allow applicants to create and manage grant applications.
* Allow applications to be saved before submission.
* Support the upload of required supporting information.
* Allow applicants to track application progress.
* Support communication between applicants and the agency.
* Provide internal staff with a structured application-review process.
* Improve consistency in assessment and approval processes.
* Improve visibility, auditability, and reporting.

## Initial User Groups

Potential user groups include:

* Prospective grant applicants
* Registered community organisation users
* Organisation administrators
* Grant assessment officers
* Program managers
* Approval delegates
* Finance officers
* System administrators

These roles are preliminary and must be validated during discovery.

## Proposed Technology

The initial technology direction is:

* Microsoft Power Pages
* Microsoft Dataverse
* Microsoft Power Automate
* Model-driven Power Apps
* Microsoft Power Platform security capabilities

Additional technologies may be introduced where justified by requirements.

## Initial Portal Capabilities

The external portal is expected to provide capabilities such as:

* Public information about grant programs
* Available grant opportunities
* Applicant registration and authentication
* Organisation profile management
* Grant application creation
* Draft application management
* Supporting-document submission
* Application submission
* Application status tracking
* Requests for additional information
* Applicant notifications
* Help and guidance

## Initial Internal Capabilities

Internal staff may require capabilities including:

* Grant program management
* Funding-round management
* Application review
* Eligibility assessment
* Assessor assignment
* Assessment and scoring
* Requests for further information
* Recommendation management
* Approval and rejection
* Payment-related processing
* Reporting
* Audit history

## Initial Design Principles

The solution should be designed around the following principles:

* Security by design
* Least-privilege access
* Clear separation between applicant-facing and internal information
* Dataverse as the authoritative business-data platform
* Server-side enforcement of important business rules
* Accessibility and usability
* Maintainability
* Auditability
* Controlled application lifecycle
* Appropriate use of native Power Platform capabilities before introducing custom development

## Open Questions

The following areas require formal discovery:

* Applicant eligibility
* Organisation registration and verification
* Relationships between contacts and organisations
* Grant program structure
* Funding-round rules
* Assessment methodology
* Approval authority
* Document requirements
* Privacy and data-retention requirements
* Accessibility requirements
* Reporting requirements
* Integration requirements
* Notification requirements
* Support model
* Expected transaction and user volumes

These questions will be investigated during the discovery and requirements phases of Project Polaris.
