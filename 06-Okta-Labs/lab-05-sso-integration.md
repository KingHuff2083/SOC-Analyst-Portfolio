# Lab 05 — Okta + Azure AD SSO Integration

**Platform:** Okta Developer Account + Microsoft Entra ID
**Duration:** ~60 minutes
**Status:** In progress

---

## Objective

Configure Okta as an Identity Provider (IdP) for Azure AD using SAML 2.0, enabling SSO so Okta users can authenticate to Azure resources. This mirrors how enterprise environments are built.

---

## Architecture
---

## Steps

### Step 1 — Add Microsoft Office 365 app in Okta
- Okta Admin → Applications → Browse App Catalog
- Search "Microsoft Office 365" → Add Integration
- Note: ACS URL and Entity ID

### Step 2 — Configure Azure AD as SAML SP
- Entra ID → Enterprise Applications → New application
- Set up SAML SSO
- Enter Okta's SSO URL and Entity ID

### Step 3 — Configure attribute mapping
- Map Okta profile fields to Azure AD claims:
  - user.email → emailaddress
  - user.displayName → name
  - user.login → UPN

### Step 4 — Test SSO flow
- Sign in via Okta → redirected to Azure → authenticated
- Check Okta System Log for SSO event
- Check Entra ID Sign-in logs for federated sign-in

### Step 5 — Document the integration

---

## Findings

*To be completed after lab*

---

## Why this is the capstone lab

This integration is how 80% of Bay Area enterprise environments are built — Okta manages the identity, Azure hosts the resources. A SOC analyst who understands both sides of this connection can investigate incidents that cross both platforms, which is exactly what real breaches do.
