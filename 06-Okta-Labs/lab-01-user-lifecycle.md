# Lab 01 — Okta Org Setup & User Lifecycle

**Platform:** Okta Developer Account (free)
**Duration:** ~30 minutes
**Status:** In progress

---

## Objective

Set up a free Okta Developer org, provision users, assign groups, and document the full user lifecycle from active to deactivated.

---

## Setup

1. Go to developer.okta.com → Create Free Account
2. Verify email → log in to Okta Admin Console

---

## Steps

### Step 1 — Create users
- Directory → People → Add person
- Create 3 users: analyst, manager, contractor
- Document: login, email, activation method

### Step 2 — Create groups
- Directory → Groups → Add group
- Create: SOC-Analysts, Contractors
- Assign users to appropriate groups

### Step 3 — Configure password policy
- Security → Authenticators → Password
- Set: min 12 chars, complexity requirements, lockout after 5 attempts

### Step 4 — User lifecycle
- Suspend the contractor user
- Deactivate the contractor user
- Document each state change and what access is removed

---

## Findings

*To be completed after lab*

---

## SOC relevance

Offboarding failures are a top cause of insider threat incidents. A SOC analyst investigating suspicious activity from a former employee needs to verify deactivation status, active sessions, and group memberships in Okta.
