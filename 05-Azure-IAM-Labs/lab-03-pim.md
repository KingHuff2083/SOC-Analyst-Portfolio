# Lab 03 — Privileged Identity Management (PIM)

**Platform:** Microsoft Entra ID — PIM
**Duration:** ~45 minutes
**Status:** In progress

---

## Objective

Configure Global Admin as a just-in-time eligible role using PIM, requiring approval and MFA to activate. Write a KQL detection for role activation events.

---

## Steps

### Step 1 — Enable PIM
- Search "Privileged Identity Management" in Azure portal
- Click Entra ID roles → Settings → Global Administrator
- Set: activation requires MFA + justification + approval

### Step 2 — Assign eligible role
- PIM → Assignments → Add assignments
- Select Global Administrator, set as Eligible (not Active)
- Set max activation duration: 1 hour

### Step 3 — Test activation flow
- Sign in as the eligible user
- Request activation: provide justification
- Approve the request as admin
- Confirm time-limited activation

### Step 4 — Document findings
*To be completed after lab*

---

## KQL — detect PIM role activation

```kql
AuditLogs
| where OperationName == "Add member to role completed (PIM activation)"
| project TimeGenerated, InitiatedBy, TargetResources, Result
| order by TimeGenerated desc
```

---

## Why this matters

Permanently assigned Global Admin is one of the most dangerous misconfigurations in Azure. PIM reduces the window of exposure to minutes instead of permanently. Any SOC analyst investigating a privilege escalation should check PIM activation logs first.
