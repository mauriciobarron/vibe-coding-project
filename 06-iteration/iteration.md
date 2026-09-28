# Iteration: Analytics, Sprint, Final Recommendation

> Module 6 · Evals & Iteration. Read the analytics, run an iteration sprint, present with evidence.

## What the evidence says

_What real usage showed: numbers if your tool has analytics, counted behaviour if it does not. Put the signal that matters on screen._

- **Primary signal:** The main constraint is currently access, not demonstrated lack of interest: enterprise SSO prevents broader testing, while the first internal user who gained access explored multiple areas of the CRM.
- **What moved:** Demo Mode removed the main access barrier by allowing users to enter the CRM directly without enterprise SSO and explore the platform with clearly labeled fictional data. Visits increased from 3 to 4, and an external tester in Switzerland was able to access and navigate beyond the login screen into areas such as the dashboard, Evidence, and Submissions. While the sample remains very small, access is no longer the primary constraint.
- **What didn't:** Usage volume is still too limited to draw conclusions about adoption or sustained engagement. The current prototype also does not yet cover the full workflow expected by the primary user: Prospect → Account → Follow-up. Prospecting and new physician creation have been added, but the Account stage still needs to support the commercial workflow, including quotations, without requiring users to re-enter information already captured during prospecting.

_No usage evidence captured yet._

## Iteration sprint

| Change | Hypothesis | Result |
|---|---|---|
| Enable frictionless access for external testers through a Demo Mode that bypasses enterprise SSO. | Removing the sign-in barrier will increase prototype access and generate enough user interaction to evaluate the CRM experience. | Pending validation — current usage is too limited to assess the hypothesis. |

## Peer feedback

Fernanda Cabrera — Physician Relationship Manager | Sep 25, 2026, 10:16 AM
“The CRM flow I would expect is: Prospect → Account → Follow-up.”
The primary internal user successfully accessed and explored the CRM, with her feedback now focused on building additional capabilities on top of the existing prototype to better address her current workflow and pain points. The CRM already supports Prospect and Follow-up, covering two of the three stages she identified. The main remaining gap is Account Management, particularly the ability to manage physicians as accounts and add quotations directly to their profiles. This provides an early qualitative signal that the core concept aligns with her day-to-day needs, while identifying a clear next layer of functionality rather than requiring a redesign of the current solution.

## The recommendation

**Decision:** ☐ Go  ☑ Iterate  ☐ Kill

_The evidence that justifies the call:_

Current testing is constrained by enterprise SSO, which limits access to @christus.mx users. One internal user successfully entered the CRM and explored multiple key pages, showing an initial signal of engagement, but the sample is too small to validate product adoption.

## Final showcase

- **Demo link:** https://circulo-christus.lovable.app/
- **The one-sentence story:** A CRM designed to help CHRISTUS teams better understand, organize, and strengthen their relationships with physicians.
- **Where it landed on the Confidence Line (M2 → now):** Early signal of value, but confidence remains limited by access friction and insufficient usage data.
