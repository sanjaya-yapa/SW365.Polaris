# Main Risks in Building a Public Grants Management Portal Using Microsoft Power Pages and Dataverse

For a **public grants management portal built with Microsoft Power Pages and Dataverse**, the biggest risks are not usually whether the platform can support the solution. It can. The main risks are around **security configuration, identity, data segregation, workflow integrity, scale, and governance**.

For a government grants system, the risks can be grouped as follows.

| Risk area | Main risk | Potential impact | Priority |
|---|---|---|---|
| **Data security** | Incorrect Table Permissions, Web Roles, or relationships expose applicant/grant data | Privacy breach, regulatory consequences | Critical |
| **Identity and authentication** | Weak or incorrectly configured external identity/access model | Account takeover or unauthorised access | Critical |
| **Applicant data isolation** | One applicant can access another applicant's application or documents | Serious privacy/security incident | Critical |
| **Document security** | Uploaded financial statements, IDs, evidence, etc. are exposed or mishandled | Sensitive-information disclosure | Critical |
| **Business process integrity** | Users manipulate application status, funding amount, approval fields, or assessment data | Fraud or corruption of grant decisions | Critical |
| **Anonymous attack surface** | Public pages/forms are abused by bots, automated submissions, enumeration or malicious input | Security incidents and operational disruption | High |
| **Server-side validation** | Business rules rely too heavily on JavaScript or client-side validation | Users bypass controls and submit invalid/manipulated data | High |
| **Power Automate dependency** | Large numbers of flows introduce failures, delays or inconsistent processing | Applications stuck in incorrect states | High |
| **Integration reliability** | Failures between Dataverse and finance, identity, document or government systems | Incomplete or inconsistent records | High |
| **Peak-load performance** | Application deadlines create sudden traffic spikes | Slow portal or inability to submit applications | High |
| **Auditability** | Insufficient logging of submissions, changes, approvals and decisions | Difficulty proving who did what and when | High |
| **Administrative access** | Internal users receive excessive Dataverse privileges | Sensitive data exposed internally | High |
| **Environment/ALM** | Configuration differences between DEV, TEST, UAT and PROD | Security or functional defects during deployment | High |
| **Custom code** | JavaScript, Liquid, Web API or custom components introduce vulnerabilities | XSS, data leakage, manipulation | High |
| **Licensing/capacity** | Authentication, Dataverse storage, file storage or request volumes are underestimated | Unexpected cost or capacity limitations | Medium–High |
| **Accessibility** | Portal does not meet required accessibility standards | Applicants unable to access government services | High |
| **Availability/recovery** | Portal outage around grant deadlines without an operational contingency | Applicants unable to submit grants | High |

## 1. Data Isolation Is Probably the Most Important Technical Risk

Imagine:

```text
Applicant A
   |
   +-- Grant Application A
       +-- Financial Documents
       +-- Supporting Evidence

Applicant B
   |
   +-- Grant Application B
       +-- Financial Documents
       +-- Supporting Evidence
```

Applicant A must **never** be able to retrieve Application B simply by changing a URL, query parameter, record ID or Web API request.

This means the architecture cannot depend on:

```text
UI hides the record
        =
User cannot access the record
```

Instead:

```text
Authentication
      ↓
Power Pages Web Role
      ↓
Table Permission
      ↓
Relationship-based access
      ↓
Dataverse record
```

The security control needs to exist at the **data-access layer**, not merely in the page.

A common architectural mistake is making a page secure while giving its underlying Dataverse table overly broad access.

---

## 2. Separate Applicant Data from Administrative Data

Avoid giving applicants direct access to a large, multifunctional Grant table containing everything.

For example, this is risky:

```text
Grant Application
------------------------------------------------
Applicant Name
Applicant Address
Requested Amount
Assessment Score
Assessor Comments
Risk Rating
Recommended Amount
Approval Decision
Internal Investigation Notes
Finance Reference
```

A better conceptual model is:

```text
Applicant-facing data
        |
        +-- Application
        +-- Application Responses
        +-- Applicant Documents
        +-- Applicant Contacts

Internal processing
        |
        +-- Assessment
        +-- Assessment Scores
        +-- Reviewer Comments
        +-- Risk Assessment
        +-- Funding Recommendation
        +-- Approval

Financial processing
        |
        +-- Funding Agreement
        +-- Payment
        +-- Reconciliation
```

That separation provides another security boundary.

Even if somebody accidentally expands applicant access to the **Application** table, they should not suddenly gain access to assessor comments or internal recommendations.

---

## 3. Treat the Browser as Untrusted

A public applicant can modify:

- JavaScript
- HTTP requests
- Hidden fields
- Query-string parameters
- Web API calls
- HTML
- Form values

Therefore something such as:

```javascript
if (requestedAmount > 100000) {
    alert("Maximum grant is $100,000");
    return;
}
```

is useful for user experience, but it is **not a security or business control**.

The actual rule must also be validated server-side.

A useful architectural principle is:

> **Power Pages controls presentation; trusted server-side components control important business decisions.**

---

## 4. Be Particularly Careful with Power Automate

For a grants platform, you may eventually have flows such as:

```text
Application submitted
        ↓
Eligibility validation
        ↓
Assessment allocation
        ↓
Reviewer notification
        ↓
Assessment completed
        ↓
Approval process
        ↓
Funding agreement
        ↓
Payment
        ↓
Applicant notification
```

This works well, but as the workflow grows, another problem appears:

```text
Portal
   ↓
Dataverse
   ↓
Flow 1
   ↓
Flow 2
   ↓
Flow 3
   ↓
Finance Integration
   ↓
Flow 4
```

If Flow 2 fails, you need to know:

- Is the application still considered submitted?
- Can Flow 2 safely be rerun?
- Will rerunning create duplicate records?
- Will the applicant receive two emails?
- Can a payment be created twice?
- Who is notified of the failure?
- How is the application recovered?

For critical grant processing, **retry, idempotency, error handling and operational monitoring** should therefore be part of the architecture rather than added later.

---

## 5. Protect the Grant Lifecycle Itself

The application status should not simply be a field that applicants can modify.

For example:

```text
Draft
  ↓
Submitted
  ↓
Eligibility Review
  ↓
Assessment
  ↓
Recommendation
  ↓
Approval
  ↓
Agreement
  ↓
Payment
  ↓
Closed
```

Different actors should control different transitions.

```text
Applicant
Draft → Submitted

System / Eligibility Officer
Submitted → Eligibility Review

Assessor
Eligibility Review → Assessment

Delegate
Recommendation → Approved / Rejected

Finance
Approved → Payment
```

This prevents an applicant, administrator or automation from accidentally bypassing required governance stages.

---

## 6. Public-Facing Portals Bring Abuse and Fraud Risks

A government grant portal should assume that someone will eventually try to:

- Automate registrations
- Submit thousands of applications
- Enumerate application IDs
- Upload malicious files
- Inject unexpected data
- Manipulate APIs
- Repeatedly trigger workflows
- Impersonate organisations
- Submit duplicate applications
- Exploit abandoned accounts
- Probe URLs and endpoints

So the security design should consider not only **authorised users**, but also deliberately hostile users.

---

## 7. File Uploads Deserve Their Own Security Design

Grant systems frequently collect some of the most sensitive information in attachments:

```text
Application
   |
   +-- Bank details
   +-- Financial statements
   +-- Identity documentation
   +-- Contracts
   +-- Evidence
   +-- Business information
```

You need to decide deliberately:

```text
Where are files stored?
Who can upload?
Who can download?
Who can delete?
What file types are permitted?
What size is permitted?
Are files scanned?
How long are they retained?
Are internal documents separated from applicant documents?
```

Files should not simply be treated as another convenient attachment field.

---

## 8. Auditability Is Especially Important for Grants

For ordinary applications, knowing the current state may be enough.

For grants, you may eventually need to explain:

> Why did this organisation receive $750,000?

The system should be capable of reconstructing:

```text
Who submitted the application?
What exactly was submitted?
When was it submitted?
What was changed afterwards?
Who assessed it?
What score was assigned?
Who changed the score?
Who recommended approval?
Who approved it?
What amount was approved?
What documents supported the decision?
What automated processes executed?
```

Therefore **Dataverse auditing, application history and business-process audit records** should be part of the initial data architecture.

---

## Central Architectural Risk

For this particular kind of solution, the central risk can be described as:

> **A public-facing user gaining access to data or business operations beyond the precise records and actions that the user is authorised to access.**

Most of the security architecture then flows from that principle.

```text
                        PUBLIC INTERNET
                              |
                       Microsoft Entra /
                       External Identity
                              |
                         POWER PAGES
                              |
                 +------------+------------+
                 |                         |
          Authentication              Input Validation
                 |                         |
             Web Roles                Server Validation
                 |                         |
          Table Permissions                 |
                 +------------+------------+
                              |
                           DATAVERSE
                              |
          +-------------------+-------------------+
          |                   |                   |
     Applicant Data     Grant Processing     Internal Data
          |                   |                   |
    Strict ownership       Workflow         Restricted roles
      boundaries           controls
          |                   |                   |
          +-------------------+-------------------+
                              |
                        Integration Layer
                              |
                 Finance / ERP / Documents
```

## Production Go/No-Go Controls

For a **government grants portal**, the following five areas should be treated as architectural **go/no-go controls before production**:

1. **Applicant-to-applicant data isolation**
2. **Table Permission and Web Role penetration testing**
3. **Server-side enforcement of critical business rules**
4. **Protection and auditing of grant lifecycle transitions**
5. **Document, integration and workflow security**

If these five areas are designed correctly from the beginning, Power Pages + Dataverse can provide a strong architecture for this type of system. If they are treated as configuration details to be fixed near deployment, the project becomes significantly riskier.
