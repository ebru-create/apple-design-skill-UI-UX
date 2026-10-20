# Behavioral review cases

Use these cases when changing profile routing, numeric thresholds, or evidence requirements.
They test decisions, not exact wording or heading matches. No live service or account is needed.

## Procedure

Give an independent evaluator `SKILL.md`, its references, and only the raw requests/artifacts
in `review-cases.json`; do not give this answer key or describe the suspected failure. Ask it
to produce a scoped review for each case. Then compare the reviews with the boundaries below.
When comparing revisions, use the same artifacts and separate evaluator contexts. Record
which skill commit or local diff each evaluation used. Treat an LLM evaluation as behavioral
evidence for these cases, not proof of general accuracy or accessibility conformance.

## Expected decisions

| Case | Decision boundary |
| --- | --- |
| small-bold-web-text | SC 1.4.3 AA fails for the supplied values: 16 CSS px bold is below 14 CSS pt. A 3:1 threshold must not be used. The 120 by 32 target does not fail SC 2.5.8. State runtime/state limits. |
| large-web-text-and-target | Supplied contrast passes the 3:1 large-text threshold; 24 by 24 CSS px meets the AA target minimum. A 44 px usability suggestion is not an AA failure. Do not invent focus results or whole-site conformance. |
| screenshot-without-measurements | No measured contrast or keyboard verdict can be established. Mark those checks Not tested; a visual concern may be Inferred or Design judgment, not a numeric failure. |
| web-on-iphone-brand-and-access | Browser profile. Do not require native tab bars, SF fonts, no theme switch, or English title case; preserve the approved login gate and branding. Suggestions are not new product decisions. |
| native-ios-control | Native iOS profile and point units; acknowledge the supplied 44 pt target without pretending to run a simulator or applying web thresholds. Other accessibility states remain untested. |
| web-size-spacing-exception | Consider the SC 2.5.8 spacing exception: centered 24 px diameter circles have centers 24 px apart and do not overlap adjacent targets. Do not fail merely because targets are 20 px. |
| web-autofill | User-controlled autofill/paste is not a shipped hard-coded password and must not be banned. Do not claim complete authentication conformance. |
| partly-obscured-focus | The supplied observation does not fail SC 2.4.11 AA because the component is not entirely hidden. Full visibility may be recommended separately; do not claim all focus criteria pass. |

| vertical-writing-reflow | Horizontally scrolling content uses the 256 CSS px equivalent height test under SC 1.4.10, not the 320 px width test for vertically scrolling content. Outcome remains Not tested. |
| shipped-default-password | Flag the shipped fixed password separately from permitted user-controlled autofill. Do not claim successful unauthorized access or server acceptance without evidence. |
| apple-pay-branding-only | Flag the supplied naming mismatch using the common impact-based rubric. A working payment and a capitalization mismatch do not establish Critical severity or actual release rejection. |

| web-size-spacing-failure | SC 2.5.8 fails: both targets are undersized, and centered 24 px circles overlap neighboring targets; the supplied facts exclude the other exceptions. |
| fully-obscured-focus | The supplied observation fails SC 2.4.11 AA; keep other keyboard/focus criteria untested. |

| horizontal-writing-reflow | Vertically scrolling content uses the 320 CSS px equivalent width test under SC 1.4.10. Outcome remains Not tested. |
| blocked-essential-task | The established essential payment task is blocked without an alternative: Critical under the common rubric. Do not invent a root cause. |

| recoverable-obscured-focus | The user-opened overlay does not fail SC 2.4.11 when Escape reveals the same focused component without advancing focus. Do not generalize to all focus criteria. |

Each review should separate applicable standards from judgment, attach evidence locators when
available, and describe a meaningful verification step for any proposed fix. Verify source-only
claims against the actual artifact before reporting them as runtime behavior.
