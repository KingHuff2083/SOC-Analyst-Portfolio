# Lab 04 — Sign-on Policy & App Assignment

**Platform:** Okta Developer Account
**Duration:** ~45 minutes
**Status:** In progress

---

## Objective

Create a sign-on policy enforcing MFA for a specific application, assign the app to a group, and document the zero trust access control model.

---

## Steps

### Step 1 — Add a test application
- Applications → Browse App Catalog → add a SAML app
- Or create a custom Bookmark app for testing

### Step 2 — Create sign-on policy
- Application → Sign On tab → Add rule
- Rule: If user is not on a trusted network → require MFA
- Rule: If user is a Contractor group member → deny access

### Step 3 — Assign app to group
- Application → Assignments → Assign to Groups
- Assign SOC-Analysts group
- Verify Contractors are excluded

### Step 4 — Test access
- Sign in as SOC analyst → MFA prompted → access granted
- Sign in as contractor → access denied
- Screenshot both outcomes

---

## Findings

*To be completed after lab*

---

## Audit documentation format
