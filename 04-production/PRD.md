# Living PRD

> Module 4 · Production Specs. Refactor for readability; extract a living PRD that stays true as the build evolves.

## Problem

_What user problem does this solve? Tie to the validated hypothesis._

Physician Relations representatives are expected to maintain physician relationships in a CRM, but the CRM costs more time than it returns. Evidence carried in the prototype: eight required fields for a single update, ~11 minutes average time to update a record against a 2-minute target, 63% of representatives keeping a shadow spreadsheet, and 18% weekly active adoption across licensed users. The result is stale physician records, invisible follow-ups, and planning done outside the system.

Validated hypothesis. If logging and planning are reduced to the representative's own daily work — a prioritised panel, two-field contact logging, and a scheduled route for the day — then weekly physician contact and profile maintenance rise above the pilot floor. The prototype made this observable: a kill switch fails the pilot at ≤20% of assigned physicians contacted per week or <30% of profiles updated per week, and logging a single contact in the prototype moved the weekly contact signal from 17% to 25%, crossing the threshold live. The problem is therefore framed as an adoption problem, not a data-model problem.

## Users & jobs

- **Primary user:** Physician Relations representative managing an assigned panel of ~12–60 physicians across CHRISTUS MUGUERZA hospitals in a metro region. Field-based, mobile-first mindset, low tolerance for forms.
- **Job to be done:** At the start of my day, tell me which physicians need me, let me book them into a realistic day of visits and calls, and let me record what happened in seconds — without leaving the tool or keeping a parallel spreadsheet.

## Scope

- **In:** Today: prioritised follow-up queue, weekly signal band with kill-switch thresholds, add-to-schedule selection.
Schedule: day strip, selected physicians only, recommended times, visit typing, overlap and location rules, unable-to-schedule state.
Planned Route: ordered in-person stops, distance and travel time per leg, outlier flagging, route confirmation.
My Physicians: search, filter, grid/list catalogue.
Physician profile: seven-stage relationship journey with reason-required transitions, activity timeline with filters, metric cards and historical charts, inline detail editing.
Contact logging: channel + note, optional next action and due date.
Evidence: weekly adoption, time-to-log, activity rate, profile completeness.
- **Out (explicitly):** Persistence, accounts, authentication, roles and permissions.
Real integration with the hospital CRM, EMR, billing, or referral systems.
Real mapping, geocoding, or traffic-aware routing.
Multi-representative collaboration, territory assignment, notifications, email/WhatsApp sending.
Mobile native app, offline mode, exports, audit trail, localisation beyond English UI.

## Requirements

| # | Requirement | Priority | Acceptance criteria |
|---|---|---|---|
| 1 | Prioritised Today queue | Must | Physicians are ordered by follow-up urgency; each row shows name, specialty, hospital, follow-up context, pending-action tag, a circular days-since-contact badge (0–20 green, 21–30 yellow, 31+ red) and a labelled productivity block with trend. |
| 2 | Relationship journey | Should | Seven stages (Identified → Assigned → Contacted → In Evaluation → Invited → Onboarded → Active); the current stage is highlighted; a stage change requires a short reason and is recorded in activity history. |

## Data & events

_What gets stored, what gets tracked._

Entities (prototype shapes).

Physician — id, name, specialty, hospital, city, phone, email, office, preferred channel, referrals this month, referral trend, days since last contact, contacted-this-week, profile-updated-this-week, priority reason, open commitment, contact history.
Contact entry — id, days ago, channel (Visit / Call / WhatsApp / Email), note, outcome, representative, next action, due date.
Schedule entry — id, physician id, day (Mon–Fri demo week), time, visit type, status (draft / booked / unable), from-Today flag, order.
Route stop — derived from booked, on-route schedule entries: order, distance from previous, travel minutes, outlier flag, kept-in-route flag.
Stage transition — stage, reason, timestamp; written into activity history.
Events worth instrumenting in a real build. physician_viewed, contact_logged (channel, seconds to complete), profile_field_updated, physician_added_to_schedule, visit_scheduled (type, recommended vs manual slot), overlap_blocked, marked_unable_to_schedule, route_confirmed (stops, km, minutes), outlier_kept / outlier_rescheduled, stage_changed (from, to, reason present), evidence_filter_applied.

What is real vs mocked in the prototype.

Real behaviour: all interaction logic — prioritisation order, selection gating, recommendation ranking, overlap and location rules, route ordering and outlier detection, stage transitions with required reasons, signal recalculation after logging, filters and charts recalculating from the in-memory data.
Mocked: every value. Twelve fictional physicians, contact histories, referral trends, revenue/HOI/engagement/CSAT/NPS/procedure figures, availability slots, and the Evidence series. Hospital coordinates are invented points on a stylised SVG map; distances are Euclidean × a constant and travel minutes a linear formula — no real map, geocoding or traffic. Portraits are generated illustrations. The demo week is fixed (Mon 14 – Fri 18 Sep 2026) rather than the real date. The only representative is a single hard-coded persona; there is no auth. Nothing persists — a refresh resets all state.

## Open questions

Where does the physician panel of record live, and is this tool the writer or a read-through layer over the existing CRM?
Which system supplies referral volume, revenue and outcome metrics, and at what refresh cadence? Several profile metrics have no confirmed source today.
Are physician addresses and hospital locations reliable enough to route on, and who owns fixing the physicians that lack a valid location?
Should scheduled visits sync to the representative's real calendar and, where relevant, the physician's office?
Do the seven relationship stages match how the business already reports on physician onboarding, and who can change a stage?
What is the correct definition of "profile updated" for the 30% threshold — any field, or a defined set of required fields?
Privacy and compliance posture: what physician and patient-derived data may be shown on a mobile device in the field?
Is the 20% / 30% kill switch the right pilot bar, measured over how many weeks and how many representatives?
Offline behaviour: representatives log from hospital corridors — is queued offline logging a launch requirement?
Who administers panel assignment when territories change mid-pilot?
