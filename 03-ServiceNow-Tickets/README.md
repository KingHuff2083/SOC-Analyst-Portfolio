# ServiceNow Ticket Lifecycle — SOC Incident Documentation

**Platform:** ServiceNow Personal Developer Instance
**Scenario:** Phishing alert from Sentinel — full ticket lifecycle

## Stage 1 — Ticket creation

| Field | Value |
|---|---|
| Category | Security |
| Subcategory | Phishing |
| Priority | 2 — High |
| Short description | Suspected phishing — anomalous sign-in — user@domain.com |

## Stage 2 — Work notes

**Note 1:** Sentinel incident assigned. Sign-in from Romania for user@domain.com. Beginning investigation.

**Note 2:** KQL confirmed successful sign-in. MFA not enforced (singleFactorAuthentication). Suspicious.

**Note 3:** AuditLogs show new MFA method added by attacker at 14:35 UTC. Escalating to Tier 2.

## Stage 3 — Escalation

| Field | Value |
|---|---|
| Priority | 1 — Critical |
| Assignment group | SOC Tier 2 |

**Escalation note:** MFA bypassed, attacker added persistence. Recommend: disable account, revoke sessions, remove MFA method.

## Stage 4 — Resolution

**Resolution notes:** Account disabled 15:10 UTC. Sessions revoked. Attacker MFA removed. Credentials reset. Account re-enabled 16:45 UTC after MFA re-registration. MTTR: 38 minutes.
