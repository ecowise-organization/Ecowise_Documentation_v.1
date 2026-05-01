# UAT feedback

This document records three rounds of user acceptance testing performed on the Ecowise
platform. Per round it lists the scripted tasks, participant counts, severity rubric, and
findings. Participant identities are sanitised.

## Table of contents

- [Methodology](#methodology)
- [Round 1 — early functional walkthrough](#round-1--early-functional-walkthrough)
- [Round 2 — role-specific deep-dives](#round-2--role-specific-deep-dives)
- [Round 3 — pre-submission polish](#round-3--pre-submission-polish)
- [Cross-round trends](#cross-round-trends)
- [Related documentation](#related-documentation)

## Methodology

Participants were briefed, given scripted tasks per role, and observed completing them.
Findings were tagged with severity:

| Severity | Meaning |
| --- | --- |
| S1 — blocker | Cannot complete the task at all. |
| S2 — major | Task completes but with significant friction or workaround. |
| S3 — minor | Cosmetic, copy, or non-blocking confusion. |
| S4 — nice-to-have | Suggestion not tied to a current task failure. |

## Round 1 — early functional walkthrough

- **Participants**: 6 — 2 individuals, 2 organisations, 1 government, 1 administrator.
- **Tasks**: signup, complete profile, browse projects/issues, send a message.

| Severity | Finding | Status |
| --- | --- | --- |
| S2 | Skill picker on signup loaded slowly and confused users | resolved — cached catalogue |
| S2 | Profile completion percentage unclear | resolved — meter added |
| S3 | Login error copy too generic | resolved |
| S4 | Suggested chat prompts on per-project bot | adopted |

## Round 2 — role-specific deep-dives

- **Participants**: 8 — 3 organisations, 2 individuals, 1 government, 1 investor, 1 admin.
- **Tasks**: end-to-end project creation with AI, run analysis, accept solution, pledge,
  promote.

| Severity | Finding | Status |
| --- | --- | --- |
| S2 | AI generator output did not show progress; users thought it had hung | resolved — busy state added |
| S2 | Project plan flow chart unreadable on smaller laptops | resolved — Dagre layout retuned |
| S3 | Investor role enable button label ambiguous | resolved — copy updated |
| S3 | Pledge inbox missing pledger names | resolved |

## Round 3 — pre-submission polish

- **Participants**: 5 — across all roles.
- **Tasks**: full happy paths plus exception flows (cancel events, withdraw pledges,
  reject verifications).

| Severity | Finding | Status |
| --- | --- | --- |
| S3 | Mobile back button contrast on a few screens | resolved — global `ink800` audit |
| S3 | Calendar view crowded on the same-day conflict | open — UI follow-up |
| S4 | Investor "lane" toggle on dashboard discoverability | open |

## Cross-round trends

- Loading and progress states were the most consistent friction across rounds — adding
  spinners and skeletons resolved most.
- Copy changes (button labels, error messages) accounted for roughly a third of findings.
- No round produced an S1 blocker, suggesting the happy paths are solid.

## Related documentation

- [test-logs.md](test-logs.md)
- [user-manual.md](user-manual.md)
- [requirements.md](requirements.md)
- [Back to index](README.md)
