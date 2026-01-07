# Security Design & Controls

This document outlines the security approach implemented in the
FD Commission Power App to ensure data integrity, access control,
and safe usage within an organizational environment.

> ⚠️ Note: This application is shared for learning and portfolio
> purposes only. All organization-specific credentials and sensitive
> data have been removed.



 1. Authentication & Access Control

 Branch-Based Login
- Users are required to select their **Branch** and log in using
  valid credentials.
- Login validation is handled through a secure data source
  (SharePoint list / Dataverse table).
- Unauthorized users cannot access the main application screens.

 Session Control
- User identity is stored in app variables after login.
- Logout clears session variables to prevent reuse on shared systems.



 2. Role-Based Authorization

Different access levels are enforced within the app:

| Role | Permissions |
|----|------------|
| Branch User | Submit FD payout requests |
| Verifier | Review and verify submitted requests |
| Admin | Full access including approvals and monitoring |

- Screen visibility and actions are controlled using Power Fx conditions.
- Users can only view and act on records relevant to their role.



 3. Data Access Restrictions

- Branch users can view **only their own branch records**.
- Filtering is applied at gallery and form level to prevent cross-branch access.
- Edit and delete permissions are restricted based on status and role.



4. Data Validation & Integrity

- Mandatory fields are enforced before submission.
- Numeric and date validations are applied to prevent incorrect entries.
- Commission amount is auto-calculated to avoid manual manipulation.
- Status fields are system-controlled and not editable by branch users.



 5. Approval Workflow Security (Power Automate)

- Approval flows are triggered only after valid form submission.
- Flow actions are restricted to authorized connectors.
- Approval decisions are logged with user and timestamp details.


 6. Audit & Traceability

Each record captures:
- Submitted By
- Submitted Date & Time
- Verified By
- Current Status

This ensures:
- Full audit trail
- Accountability
- Easy tracking of approvals and changes



 7. Data Protection & Privacy

- No passwords or secrets are hardcoded in the app.
- Sensitive organizational identifiers are excluded from this repository.
- Demo or placeholder data is used for public sharing.
- App follows least-privilege access principle.


 8. Deployment & Repository Safety

- This GitHub repository does not contain:
  - Live production data
  - Tenant IDs
  - Real user credentials
  - Environment-specific secrets
- The `.msapp` file is provided strictly for reference and re-import purposes.


 9. Disclaimer

This project is intended for:
- Learning
- Documentation
- Portfolio demonstration

It is not intended for direct production deployment without
proper security review and environment-specific configuration.


Author:Akash Sontakke  
Platform: Microsoft Power Apps (Canvas App)

