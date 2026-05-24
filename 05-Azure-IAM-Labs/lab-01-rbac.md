# Lab 01 — User Provisioning & RBAC

**Platform:** Microsoft Entra ID (Azure AD)
**Duration:** ~30 minutes
**Status:** In progress

---

## Objective

Demonstrate the principle of least privilege by creating users with different role assignments and documenting the security implications of over-privileged access.

---

## Steps

### Step 1 — Create test users
- Navigate to Entra ID → Users → New user
- Create two users: `analyst-read@domain.com` and `analyst-admin@domain.com`
- Document: display name, UPN, initial password

### Step 2 — Assign Reader role (least privilege)
- Go to Subscriptions → Access control (IAM) → Add role assignment
- Assign `Reader` to `analyst-read@domain.com`
- Scope: Resource group level only

### Step 3 — Assign Contributor role (over-privileged example)
- Assign `Contributor` to `analyst-admin@domain.com`
- Scope: Subscription level
- Document why subscription-level Contributor is dangerous

### Step 4 — Verify and document
- Log in as each user and confirm access matches role
- Screenshot the role assignments blade
- Write findings below

---

## Findings

*To be completed after lab*

---

## MITRE ATT&CK connection

- T1078 — Valid Accounts: over-privileged accounts increase blast radius of credential compromise
- T1098 — Account Manipulation: attackers escalate privileges by modifying role assignments

---

## KQL — detect new role assignments

```kql
AuditLogs
| where OperationName == "Add member to role"
| project TimeGenerated, InitiatedBy, TargetResources, Result
| order by TimeGenerated desc
```
