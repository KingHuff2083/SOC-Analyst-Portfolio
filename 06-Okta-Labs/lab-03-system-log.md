# Lab 03 — Okta System Log Investigation

**Platform:** Okta Admin Console → System Log
**Duration:** ~45 minutes
**Status:** In progress

---

## Objective

Use the Okta System Log to investigate a suspicious sign-in event — same workflow a SOC analyst performs daily at Okta-based organizations.

---

## Key System Log event types

| Event type | What it means |
|---|---|
| user.session.start | User signed in |
| user.session.end | User signed out |
| user.authentication.sso | SSO authentication |
| policy.evaluate_sign_on | Sign-on policy evaluated |
| user.account.lock | Account locked out |
| security.threat.detected | Okta ThreatInsight flagged |
| user.mfa.factor.activate | New MFA factor enrolled |

---

## Investigation steps

### Step 1 — Access System Log
- Reports → System Log
- Set time range: last 24 hours

### Step 2 — Filter for suspicious sign-in

Search for:~
Look for:
- Unfamiliar IP address
- Unusual time of day
- New device / user agent

### Step 3 — Investigate the event

Click the event → expand details:
- actor.displayName — who signed in
- client.ipAddress — from where
- client.geographicalContext — location
- device.os — what device
- authenticationContext.authenticationStep — MFA used?

### Step 4 — Check for follow-on activity

Filter for same user after the suspicious sign-in:
- New MFA factor enrolled? (user.mfa.factor.activate)
- Password changed? (user.account.update_password)
- New app assigned? (application.user_membership.add)

### Step 5 — Write triage report

Use the same format as the Sentinel investigation in folder 01.

---

## Findings

*To be completed after lab*
