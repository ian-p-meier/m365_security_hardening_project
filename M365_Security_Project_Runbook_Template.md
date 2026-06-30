# M365 Tenant Security Hardening — Project Runbook

## How to Use This Document
This is a working log, not a polished deliverable. Fill it in as you go (or retroactively from what you've already built). Be specific — exact policy names, exact settings, exact numbers. Vague entries ("configured Conditional Access") are useless later; specific entries ("required MFA for all users except break-glass account, blocked legacy auth") are gold for interviews and for writing the executive summary later.

For every section below, capture: **what you did**, **why you did it**, **what you considered/rejected**, and **the result**. The "why" and "what you rejected" are what prove judgment, not just execution.

---

## 1. Project Overview
- Goal of the environment (e.g., "stand up a clean M365 tenant and harden it to a high Secure Score, simulating a small business / SMB client environment")
- Starting point (fresh tenant? trial license tier used — e.g., M365 Business Premium?)
- Scope / what's in vs. out (e.g., "single tenant, ~X simulated users, no hybrid AD")
- Tools/licenses used (Entra ID P1/P2, Defender for Business/MDE, Intune, etc.)

## 2. Secure Score Tracking
| Date | Secure Score | Notes / What changed |
|------|-------------|----------------------|
| | | Baseline / starting score |
| | | After identity hardening |
| | | After endpoint hardening |
| | | Final |

(Screenshot the Secure Score page at each milestone — save images alongside this doc.)

## 3. Identity & Access
For each item: policy name, what it does, why, what you considered instead, result/screenshot reference.

- **Conditional Access policies** (list each one individually)
- **MFA enforcement** (method required, any exclusions, break-glass account setup)
- **Legacy authentication** (blocked? how?)
- **Privileged role management** (PIM used? admin role assignments?)
- **Password policy / self-service reset**

## 4. Endpoint Management (Intune / Defender)
- **Device compliance policies** (what's required to be "compliant" — encryption, OS version, etc.)
- **Configuration profiles** (what's enforced on devices)
- **App protection policies** (if applicable)
- **Defender for Endpoint / MDE onboarding** (what tier, what's monitored)
- **Patch management approach**

## 5. Data Protection
- **Sharing/external collaboration settings** (SharePoint/OneDrive external sharing rules)
- **DLP policies** (if configured)
- **Retention/audit log settings**
- **License assignment strategy** (groups vs. individual, why)

## 6. Monitoring & Alerting
- **Alert policies configured**
- **Audit log retention**
- **Any Sentinel/Defender XDR integration** (if applicable)

## 7. Problems & Decisions (this section matters most for interviews)
For each notable issue:
- What broke or didn't work as expected
- What you tried
- What you ultimately decided and why
- What you'd do differently with more time/budget

## 8. Outcome Summary
- Final Secure Score vs. baseline
- 3-5 sentence summary of what the environment demonstrates
- What this maps to in real job terms (e.g., "equivalent to hardening identity and endpoint security for a 25-user SMB tenant")

---

## Quick Capture Checklist (do this first, in one sitting)
Before writing prose, just brain-dump answers to these — you can organize after:
- [ ] What licenses/SKUs is the tenant on?
- [ ] List every Conditional Access policy you created, in plain English
- [ ] What's your Secure Score now? What was it at the start (even roughly)?
- [ ] What Intune policies exist?
- [ ] What was the hardest thing to get working, and how did you solve it?
- [ ] What would you still add if you kept going?
