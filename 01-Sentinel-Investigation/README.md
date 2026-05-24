# Sentinel Investigation — Suspicious Sign-in from Anomalous Location

> **Status:** In progress — Azure lab being configured
> **Tool:** Microsoft Sentinel (Training Lab solution)
> **Severity:** Medium
> **Outcome:** TBD after lab completion

---

## Alert details

| Field | Value |
|---|---|
| Alert name | Sign-in from anomalous location |
| Severity | Medium |
| MITRE tactic | Initial Access |
| MITRE technique | T1078 — Valid Accounts |
| Log source | SigninLogs (Azure AD) |

---

## Investigation steps

### Step 1 — Review the alert in Sentinel
- Opened incident in Microsoft Sentinel Incidents blade
- Reviewed entities: user principal name, source IP, location
- Noted sign-in was from a country outside the user's normal pattern

### Step 2 — Query SigninLogs with KQL

```kql
cat > 02-Incident-Response-Playbook/phishing-playbook.md << 'ENDOFFILE'
# Incident Response Playbook — Phishing with Credential Theft

**Framework:** NIST SP 800-61 Rev. 2
**Scenario:** Phishing email → user clicks link → credentials harvested → attacker signs in
**Analyst level:** Tier 1 / Tier 2

---

## Attack chain (MITRE ATT&CK)

| Stage | Technique ID | Technique name | Detection source |
|---|---|---|---|
| Initial access | T1566.001 | Spearphishing link | Email gateway |
| Credential access | T1056.001 | Credential harvesting | Endpoint telemetry |
| Valid accounts | T1078 | Use of harvested credentials | SigninLogs |
| Persistence | T1098 | MFA method added by attacker | AuditLogs |
| Collection | T1114.003 | Email forwarding rule created | AuditLogs |

---

## Phase 1 — Preparation

- [ ] Sentinel connected to Azure AD SigninLogs and AuditLogs
- [ ] Defender for Endpoint deployed on all managed endpoints
- [ ] Email gateway alerts feeding into Sentinel
- [ ] On-call escalation contact list is current
- [ ] ServiceNow incident template ready

---

## Phase 2 — Detection and analysis

1. Review Sentinel alert entities: user, IP, email sender, attachment hash
2. Confirm sign-in succeeded and check for impossible travel:

```kql
cat > 03-ServiceNow-Tickets/README.md << 'ENDOFFILE'
# ServiceNow Ticket Lifecycle — SOC Incident Documentation

**Platform:** ServiceNow Personal Developer Instance (PDI)
**Scenario:** Phishing alert from Microsoft Sentinel — full ticket lifecycle
**Purpose:** Demonstrate audit-ready SOC ticket documentation

---

## Stage 1 — Ticket creation

| Field | Value |
|---|---|
| Category | Security |
| Subcategory | Phishing |
| Priority | 2 — High |
| Caller | SOC Analyst L1 |
| Short description | Suspected phishing — anomalous sign-in — user@domain.com |
| Assignment group | SOC Tier 1 |

*Screenshot: ticket creation — to be added*

---

## Stage 2 — Work notes (triage in progress)

**Work note 1 — Initial review:**
**Work note 2 — KQL results:**
**Work note 3 — Post-login activity:**
*Screenshot: work notes — to be added*

---

## Stage 3 — Escalation to Tier 2

| Field | Value |
|---|---|
| Priority | 1 — Critical |
| Assignment group | SOC Tier 2 |
| State | In progress |

**Escalation note:**
*Screenshot: escalation — to be added*

---

## Stage 4 — Resolution and closure

| Field | Value |
|---|---|
| State | Resolved |
| Resolution code | Solved (Security incident) |

**Resolution notes:**
*Screenshot: closed ticket — to be added*

---

## What this demonstrates

- ITSM ticket hygiene and SOC documentation standards
- Clear timestamped work notes at each triage step
- Correct escalation procedure with evidence and recommendations
- Audit-ready resolution notes including MTTR calculation
