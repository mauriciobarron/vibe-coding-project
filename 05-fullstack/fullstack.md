# Full-Stack: Data, Access Rules, Edge Cases, Deploy

> Module 5 · Full-Stack. Add data schemas, access rules, and edge cases; stress-test and deploy.

## Deployed link

_The working, shareable link that survives real users._

_____

## Data schema

| Entity | Key fields | Notes |
|---|---|---|
| Identity & access | profiles, representatives, user_roles, user_id, representative_id, role | Links each Microsoft-authenticated user to a physician relations representative and assigns an admin, manager, or representative role. |
| Physician engagement | physicians, contacts, appointments, hospitals, availability, metrics | Stores physician profiles, assigned representatives, interaction history, schedules, locations, availability, routes, and performance metrics. No sample data is preloaded. |

## Access rules

_Who can see / do what? Where are the auth boundaries?_

Access requires Microsoft Sign-In with an @christus.mx account; no public registration or additional two-step authentication is added. Representatives can access their assigned physicians, contacts, and appointments; managers can access their teams; admins manage representatives and roles. RLS enforces these boundaries at the database level, and users cannot assign or modify their own roles.

## Edge cases hardened

| Case | Before | After |
|---|---|---|
| Empty / first-run state | Empty accounts could show blank screens or invalid percentages. | Each screen shows a clear empty state and CTA without errors or fabricated data. |
| Bad / malicious input | Overlaps and invalid data were checked only in the browser. | Server-side validation blocks schedule conflicts, invalid locations, excessive text, and unauthorized access. |
| Failure / offline | Failed actions could disappear or appear successful until refresh. | Failed writes roll back, show an inline error with Retry, and preserve the user’s session and previous data. |

## Stress test results

_What you threw at it, and what held / broke._

_____
