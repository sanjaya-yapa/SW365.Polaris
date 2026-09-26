# Project Polaris – Available Grants Page

## Requirement Status

**Status:** Provisional requirement for Chapter 2 demonstration
**Purpose:** Demonstrate AI-assisted page generation using traditional Microsoft Power Pages.
**Important:** This requirement will be reviewed and refined during the formal requirements phase.

## Requirement

Project Polaris requires a public **Available Grants** page that introduces community organisations to currently available grant opportunities and explains how to select an appropriate grant program.

## Intended Users

* Prospective applicants
* Community organisation representatives
* Existing registered applicants

Authentication should not be required to view general information about available grant programs.

## Page Objectives

The page should:

* Clearly identify that it contains available grant opportunities.
* Explain the purpose of the grants program.
* Provide a short explanation of general eligibility.
* Explain how users can review available opportunities.
* Provide guidance on selecting an appropriate grant program.
* Provide a clear action for beginning the application process.
* Provide a link or direction to further eligibility guidance.

## Proposed Content

The page should contain:

### Page Heading

**Available Grants**

### Introduction

A short explanation that Project Polaris provides funding opportunities for eligible community organisations.

### Eligibility Overview

A short section explaining that eligibility differs between grant programs and applicants should review the requirements before starting an application.

### Available Grant Opportunities

A section reserved for displaying currently available funding opportunities.

The dynamic list of grants will be implemented later using approved Dataverse data and Power Pages configuration.

### How to Apply

Provide brief guidance describing the expected journey:

1. Review the grant opportunity.
2. Check eligibility.
3. Sign in or register.
4. Start an application.
5. Complete the required information.
6. Submit the application before the closing date.

### Call to Action

Provide an obvious action that allows an eligible applicant to proceed toward starting an application.

## User Experience Requirements

The page should:

* Use clear and concise language.
* Be suitable for members of the public.
* Avoid unnecessary technical terminology.
* Use clear headings and logical sections.
* Be readable on desktop and mobile devices.
* Follow the accessibility standards adopted by the project.

## Security Considerations

The page contains public information only.

No applicant-specific, application-specific, assessment, financial, or internal information should be displayed on this page.

Dynamic grant information will later be restricted to fields explicitly approved for public display.

## Acceptance Criteria for This Demonstration

For the Chapter 2 demonstration:

* Power Pages Copilot can generate an initial page based on the approved page description.
* The generated page contains a clear title and introductory content.
* The generated page contains sections corresponding broadly to the stated requirement.
* The result is reviewed by the developer before being retained.
* No generated content is considered an approved business statement without human review.
* No dynamic Dataverse functionality is required at this stage.
