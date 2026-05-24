# Incident Response Playbook — Phishing with Credential Theft

**Framework:** NIST SP 800-61 Rev. 2
**Scenario:** Phishing email → credentials harvested → attacker signs in

## Attack chain (MITRE ATT&CK)

| Technique ID | Technique | Detection source |
|---|---|---|
| T1566.001 | Spearphishing link | Email gateway |
| T1078 | Valid accounts | SigninLogs |
| T1111 | MFA interception (AiTM) | Identity Protection |
| T1098.005 | MFA method added | AuditLogs |
| T1114.003 | Email forwarding rule | AuditLogs |

## Phase 1 — Preparation
- [ ] Sentinel connected to SigninLogs and AuditLogs
- [ ] Defender for Endpoint deployed on all endpoints
- [ ] Escalation contact list current
- [ ] ServiceNow incident template ready

## Phase 2 — Detection and analysis

```kql
ls
exit
...
cat > 02-Incident-Response-Playbook/phishing-playbook.md << 'EOF'
# Incident Response Playbook — Phishing with Credential Theft

**Framework:** NIST SP 800-61 Rev. 2
**Scenario:** Phishing email → credentials harvested → attacker signs in

## Attack chain (MITRE ATT&CK)

| Technique ID | Technique | Detection source |
|---|---|---|
| T1566.001 | Spearphishing link | Email gateway |
| T1078 | Valid accounts | SigninLogs |
| T1111 | MFA interception (AiTM) | Identity Protection |
| T1098.005 | MFA method added | AuditLogs |
| T1114.003 | Email forwarding rule | AuditLogs |

## Phase 1 — Preparation
- [ ] Sentinel connected to SigninLogs and AuditLogs
- [ ] Defender for Endpoint deployed on all endpoints
- [ ] Escalation contact list current
- [ ] ServiceNow incident template ready

## Phase 2 — Detection and analysis

```kql
SigninLogs
| where UserPrincipalName == "<user>"
| where TimeGenerated > ago(1h)
| project TimeGenerated, IPAddress, Location, ResultType, AuthenticationRequirement
```

## Phase 3 — Containment
- [ ] Isolate endpoint in Defender for Endpoint
- [ ] Disable user account in Entra ID
- [ ] Revoke all active sessions
- [ ] Block sender domain in Defender for Office 365

## Phase 4 — Eradication
- [ ] Purge malicious emails from all mailboxes
- [ ] Remove attacker-added MFA methods
- [ ] Delete malicious inbox rules
- [ ] Reset credentials and force MFA re-registration

## Phase 5 — Recovery
- [ ] Re-enable account after reset confirmed
- [ ] Lift device isolation after clean EDR scan
- [ ] Monitor account for 72 hours

## Phase 6 — Post-incident
- [ ] Document full timeline and calculate MTTR
- [ ] Update Sentinel detection rules if needed
- [ ] File post-incident report within 5 business days
