# Lab 04 — Identity-Based Incident Investigation

**Platform:** Microsoft Sentinel + Entra ID
**Duration:** ~60 minutes
**Status:** In progress

---

## Objective

End-to-end investigation: Sentinel alert fires for anomalous sign-in → trace through SigninLogs → check IAM configuration → determine root cause → document findings.

---

## Investigation workflow

### Step 1 — Sentinel alert review
- Alert: Sign-in from anomalous location
- Review entities: user, IP, location, time

### Step 2 — SigninLogs KQL query

```kql
SigninLogs
| where UserPrincipalName == "<affected_user>"
| where TimeGenerated > ago(24h)
| project TimeGenerated, IPAddress, Location,
          ResultType, AuthenticationRequirement,
          ConditionalAccessStatus, ConditionalAccessPolicies
| order by TimeGenerated desc
```

### Step 3 — Check IAM configuration
- Was MFA enforced? (AuthenticationRequirement field)
- Did Conditional Access fire? (ConditionalAccessStatus field)
- What policies applied?

### Step 4 — Check role assignments
- Was this user over-privileged?
- Any recent role changes in AuditLogs?

### Step 5 — Check PIM activation history
- Did the user activate a privileged role around the time of the alert?

### Step 6 — Document findings and escalation decision

---

## Findings

*To be completed after lab*
