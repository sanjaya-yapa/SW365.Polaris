# Main Risks in Building a Public Grants Management Portal Using Microsoft Power Pages and Dataverse

## Main Risks

1. **Data security and unauthorised access**  
   Misconfigured table permissions, web roles, page permissions, or Dataverse security can expose applicant, financial, identity, or evaluation data. Public portals are especially vulnerable to broken access control and users accessing records through manipulated URLs or API requests.

2. **Privacy and regulatory compliance**  
   Grant applications may contain personally identifiable information, tax details, financial records, demographic data, or sensitive organisational information. Improper retention, disclosure, cross-border processing, consent, or subject-access handling can create legal and regulatory exposure.

3. **Identity and account security**  
   Weak authentication, poor external identity configuration, account takeover, duplicate accounts, and inadequate multifactor authentication can compromise applications and applicant data.

4. **Public-facing attack surface**  
   The portal may be targeted with automated account creation, credential stuffing, denial-of-service attempts, spam submissions, malicious file uploads, injection attacks, and exploitation of custom JavaScript or integrations.

5. **File-upload risks**  
   Supporting documents can contain malware, excessive file sizes, sensitive metadata, or prohibited content. Inadequate validation, scanning, storage controls, or download authorisation can create security and operational problems.

6. **Accessibility and usability failures**  
   Applicants may be unable to complete the process because of poor keyboard support, screen-reader incompatibility, insufficient contrast, inaccessible forms, unclear validation messages, or poor mobile usability. This can exclude eligible applicants and create compliance risk.

7. **Performance and scalability limitations**  
   Application deadlines can create sudden traffic spikes. Large forms, complex Dataverse queries, attachments, synchronous workflows, and external integrations may result in slow pages, timeouts, throttling, or failed submissions.

8. **Data integrity and application-state errors**  
   Grants processes often involve drafts, submissions, reviews, approvals, amendments, payments, and appeals. Poorly controlled state transitions, duplicate submissions, partial saves, concurrency issues, or inconsistent calculations can corrupt the official record.

9. **Workflow and business-rule complexity**  
   Eligibility, scoring, reviewer assignments, conflicts of interest, approvals, notifications, and payment decisions may be difficult to represent reliably. A configuration error can cause incorrect eligibility decisions, missed deadlines, or unauthorised approvals.

10. **Auditability and non-repudiation**  
    Public funding decisions require defensible records of who changed what, when, and why. Insufficient auditing, editable historical data, incomplete approval evidence, or inconsistent timestamps can undermine investigations and public accountability.

11. **Integration failures**  
    Connections to identity providers, finance systems, payment platforms, document repositories, email services, reporting tools, or government systems may fail, produce duplicates, or become inconsistent. Integration credentials and service accounts also require careful protection.

12. **Notifications and communications risk**  
    Incorrect email addresses, bounced messages, duplicate notifications, localisation errors, or failed reminders can cause applicants to miss deadlines or misunderstand decisions. Notifications may also accidentally disclose sensitive information.

13. **Dataverse capacity, licensing, and cost uncertainty**  
    Storage, file capacity, authenticated-user licensing, anonymous access, API usage, automation runs, and reporting workloads can generate costs that are difficult to predict, particularly for seasonal or high-volume programs.

14. **Configuration and customisation fragility**  
    Power Pages, Dataverse, Power Automate, plugins, JavaScript, and connectors can interact in ways that are difficult to test. Platform updates or changes to dependencies may introduce regressions or break custom behaviour.

15. **Environment and deployment risks**  
    Inadequate separation between development, test, and production environments, manual configuration, unmanaged changes, missing connection references, or incomplete deployment procedures can cause production outages or security defects.

16. **Operational support and incident response**  
    A public portal needs monitoring, alerting, backup and recovery procedures, capacity planning, support processes, and deadline-period incident response. Without these, failures may go undetected until applicants report them.

17. **Fraud and manipulation**  
    Applicants may submit false information, create multiple identities, manipulate documents, collude with reviewers, or exploit eligibility and payment rules. The system should support validation, duplicate detection, segregation of duties, and investigation workflows.

18. **Human-process and governance risks**  
    Technology cannot compensate for unclear program rules, inconsistent reviewer practices, poorly defined ownership, inadequate training, or uncontrolled changes to eligibility and scoring criteria.

19. **Reporting and transparency errors**  
    Incorrect aggregations, stale data, inconsistent definitions, or inappropriate publication of personal information can produce misleading public reports and undermine confidence in the program.

20. **Platform dependency and exit risk**  
    The organisation may become dependent on Microsoft-specific capabilities, licensing terms, connectors, and specialist skills. Future migration, major redesign, or integration with non-Microsoft systems may be costly and complex.
