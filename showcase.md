# A physician relationship CRM that helps CHRISTUS teams turn physician data and interactions into stronger, more actionable relationships.

_Product School · Vibe Coding Certification · Final Project Showcase_

**Live product:** https://circulo-christus.lovable.app/

## The Problem & Hypothesis

**Problem.** Physician Relations representatives are expected to maintain physician relationships in a CRM, but the CRM costs more time than it returns. Evidence carried in the prototype: eight required fields for a single update, ~11 minutes average time to update a record against a 2-minute target, 63% of representatives keeping a shadow spreadsheet, and 18% weekly active adoption across licensed users. The result is stale physician records, invisible follow-ups, and planning done outside the system.

Validated hypothesis. If logging and planning are reduced to the representative's own daily work — a prioritised panel, two-field contact logging, and a scheduled route for the day — then weekly physician contact and profile maintenance rise above the pilot floor. The prototype made this observable: a kill switch fails the pilot at ≤20% of assigned physicians contacted per week or <30% of profiles updated per week, and logging a single contact in the prototype moved the weekly contact signal from 17% to 25%, crossing the threshold live. The problem is therefore framed as an adoption problem, not a data-model problem.

**Hypothesis.** We believe *A streamlined physician relationship management tool that centralizes assigned physicians, prioritized follow-ups, contact history, and profile updates.* will cause *Physician relations representatives spend less time managing spreadsheets and more time engaging physicians and strengthening their relationship with CHRISTUS MUGUERZA.* for *Physician relations representatives responsible for engaging and developing high-performing physicians for Círculo CHRISTUS.*. We'll know we're right when *Representatives actively use the tool, contact their assigned physicians, log follow-up activities, and keep physician information up to date.*.

## The Evidence

Analytics: 4 visits · 13+ page views · 4.33 views/visit · 5m 33s avg. duration · 33% bounce rate. Demo Mode removed the SSO barrier, enabling external users to explore the CRM with sample data.  
User signal: Navigation expanded beyond sign-in into core CRM areas, including Dashboard, Evidence and Submissions; sample size remains too small for quantitative validation.  
Peer feedback: Fernanda Cabrera, Physician Relationship Manager — “The CRM flow I would expect is: Prospect → Account → Follow-up.” Prospect and Follow-up are already supported; her feedback identified Account Management and physician quotations as the next capability to build.  
Evidence: Feedback is shifting from access and core usability toward additional features that address real workflow needs—an early qualitative signal of relevance, but not yet enough evidence to validate adoption.

## Data Signal → The One Fix

| Change | Hypothesis | Result |
| Enable frictionless access for external testers through a Demo Mode that bypasses enterprise SSO. | Removing the sign-in barrier will increase prototype access and generate enough user interaction to evaluate the CRM experience. | Pending validation — current usage is too limited to assess the hypothesis. |

## The Recommendation

**Verdict: ITERATE, keep refining.**

**Decision:** ☐ Go ☑ Iterate ☐ Kill

Current testing is constrained by enterprise SSO, which limits access to @christus.mx users. One internal user successfully entered the CRM and explored multiple key pages, showing an initial signal of engagement, but the sample is too small to validate product adoption.

## My Story, Friction · Learning · Aha

- **Demo link:** https://circulo-christus.lovable.app/
- **The one-sentence story:** A CRM designed to help CHRISTUS teams better understand, organize, and strengthen their relationships with physicians.
- **Where it landed on the Confidence Line (M2 → now):** Early signal of value, but confidence remains limited by access friction and insufficient usage data.

---
_Built across six modules with an AI build tool, then iterated from live product data. Hosted on GitHub Pages._
