# MITRE ATT&CK Mapping — Phishing to Account Takeover

**Framework:** ATT&CK v14

## Attack narrative

Attacker sends phishing email with link to fake M365 login page. User enters credentials. Attacker signs in from overseas IP, bypasses MFA via AiTM session token replay, adds new MFA method for persistence, creates mail forwarding rule to exfiltrate email.

## Technique mapping

| Technique | Tactic | Detection | Mitigation |
|---|---|---|---|
| T1566.001 Spearphishing link | Initial Access | Defender for O365 | Safe Links + user training |
| T1078 Valid accounts | Initial Access | Sentinel SigninLogs | MFA + Conditional Access |
| T1111 MFA interception | Credential Access | Identity Protection | FIDO2 phishing-resistant MFA |
| T1098.005 Device registration | Persistence | AuditLogs | MFA registration policy |
| T1114.003 Email forwarding | Collection | AuditLogs | Block external forwarding |

## Detection KQL — anomalous sign-in

```kql
SigninLogs
| where TimeGenerated > ago(1h)
| where UserPrincipalName == "<affected_user>"
| where AuthenticationRequirement == "singleFactorAuthentication"
| project TimeGenerated, UserPrincipalName, IPAddress, Location, ResultType
```

## Key interview talking point

Standard TOTP MFA does not protect against AiTM attacks — session tokens can be stolen even after MFA completes. The only reliable mitigation is phishing-resistant MFA (FIDO2 / Windows Hello), which binds authentication to the origin URL and cannot be intercepted by a proxy. This is a real detection gap in many organizations.
