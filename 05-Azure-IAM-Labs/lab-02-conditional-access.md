# Lab 02 — Conditional Access Policies

**Platform:** Microsoft Entra ID
**Duration:** ~45 minutes
**Status:** In progress

---

## Objective

Build three Conditional Access policies that enforce MFA, block legacy authentication, and restrict sign-ins by location.

---

## Policy 1 — Require MFA for all users

**Settings:**
- Users: All users
- Cloud apps: All cloud apps
- Grant: Require MFA

**ATT&CK mitigation:** T1078 — Valid Accounts

---

## Policy 2 — Block legacy authentication

**Settings:**
- Users: All users
- Conditions → Client apps: Exchange ActiveSync, Other clients
- Grant: Block access

**Why:** Legacy auth protocols do not support MFA — attackers use them to bypass modern auth controls.

**ATT&CK mitigation:** T1133 — External Remote Services

---

## Policy 3 — Block sign-ins outside United States

**Settings:**
- Users: All users
- Conditions → Locations: Include Any location, Exclude United States
- Grant: Block access

**ATT&CK mitigation:** T1078 — anomalous location sign-ins

---

## Findings

*To be completed after lab*

---

## KQL — detect Conditional Access failures

```kql
SigninLogs
| where ConditionalAccessStatus == "failure"
| project TimeGenerated, UserPrincipalName, IPAddress,
          Location, ConditionalAccessPolicies
| order by TimeGenerated desc
```
