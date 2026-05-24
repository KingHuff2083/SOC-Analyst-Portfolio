# Lab 02 — MFA Enrollment & Authenticator Policies

**Platform:** Okta Developer Account
**Duration:** ~30 minutes
**Status:** In progress

---

## Objective

Configure Okta Verify MFA, enforce enrollment for all users, and document what happens when MFA is not enrolled.

---

## Steps

### Step 1 — Enable Okta Verify
- Security → Authenticators → Add Authenticator → Okta Verify
- Enable: Push notifications + TOTP

### Step 2 — Create authenticator enrollment policy
- Security → Authenticators → Enrollment tab
- Create policy: Required for Everyone
- Set: Okta Verify required, SMS optional

### Step 3 — Test enrollment flow
- Log in as a new user
- Complete Okta Verify enrollment on mobile
- Screenshot enrollment confirmation

### Step 4 — Test unenrolled user
- Create user without MFA enrolled
- Attempt sign-in and document what Okta does
- Screenshot the blocked access screen

---

## Findings

*To be completed after lab*

---

## MITRE ATT&CK connection

- T1111 — MFA interception: understanding MFA enrollment helps SOC analysts detect when attackers register their own authenticator
- T1098.005 — Device registration: same technique applies in Okta when attacker enrolls a new Okta Verify device
