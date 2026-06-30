#This is a work in progress with instructions on what needs to happen

# M365 Tenant Security Hardening — Project Runbook

## How to Use This Document
This is a working log, not a polished deliverable. Fill it in as you go (or retroactively from what you've already built). Be specific — exact policy names, exact settings, exact numbers. Vague entries ("configured Conditional Access") are useless later; specific entries ("required MFA for all users except break-glass account, blocked legacy auth") are gold for interviews and for writing the executive summary later.

For every section below, capture: **what you did**, **why you did it**, **what you considered/rejected**, and **the result**. The "why" and "what you rejected" are what prove judgment, not just execution.

---

## 1. Project Overview
- Goal of the environment: To create a consistent M365 Environment from Scratch to be as secure as possible while not increasing friction
- Starting point: Fresh Tenant with M365 Business Premium and Micrsoft Defender for Endpoint Plan 2
- Scope: Single Tenat, no B2B collaborations, Cloud Native devices and applications. Microsoft EcoSystem
- Tools/licenses used: Microsoft M365 Business Premium, Microsoft Defender for Endpoint Plan 2

## 2. Secure Score Tracking
| Date | Secure Score | Notes / What changed |
|------|-------------|----------------------|
|4/19/26 |66% | Baseline / starting score |
|4/20/26 |68% | After identity hardening |
|6/28/26 |72% | After endpoint hardening |
|6/30/26 |72% | Final |

## 3. Identity & Access
For each item: policy name, what it does, why, what you considered instead, result/screenshot reference.

- **Conditional Access policies**
- **MFA enforcement** All Users require a form of MFA configure by the Authentication Methods Policies
- **Legacy authentication** Blocked Legacy Authentication preventing Exchange ActiveSync Cliets as well as other clients for Authenticating to that account
- **Require MFA for All Admins** Admins must have a form of MFA configured by the Authentication Methods Policies
- **Require MFA for All Guests** Guest users must register a valid form of MFA.
- **Device Compliance for Access to Resources** Requires a device to be marked as compliant in order to access resources
- **No Persistent Browser Session** Prevents a browser from staying in session will also require a browser sign in to occur every 4 hours if the browser is open.
- **Session Timeout Admin Portal** Does not allow an Admin to have the portal open for longer that 1 hour
- **Authentication Stregnth Admins (TESTING)** Reporting only on Passwordless authentication
- **Privileged role management** - Assigned Unlicensed users, currently testing stronger authentication to verify a more robust sign in request
- **Password policy / self-service reset** - Configured for all users requiring two methods of MFA (Retiring security questions, ran into errors on the disabling of the option)

## 4. Endpoint Management (Intune / Defender)
- **Device compliance policies**: For a device to be compliant, the following must be true: Secure Boot Enabled, Code Integrity Enabled, BitLocker configured, Running Windows 10.0.22621, TPM must be enabled, Microsoft Security Settings all enabled, prevent simple passwords, must have at least 8 characters, and the device is not listed no higher than Medium in M365 Defender for Endpoint.
- **Configuration profiles**: Devices have the following configured: Windows Attack Surface Reduction Policies (Provides foundational protection against malicious activities
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
