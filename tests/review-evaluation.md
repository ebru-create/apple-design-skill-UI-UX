# Scoped behavioral evaluation

Evaluated on 2026-10-20 against base commit
`914b6a377c22755597e4405e54911b996de822d7` and the candidate change accompanying this record.

Separate independent LLM evaluator contexts received each skill entrypoint, relevant references,
and raw cases only, without the answer key or suspected failures. Their responses were compared
with the expected decision boundaries in `review-cases.md`.

| Scope | Base | Candidate |
| --- | --- | --- |
| First eight cases in `review-cases.json` | 8 of 8 core decisions matched | 8 of 8 core decisions matched |
| Eight added cases: both reflow directions, shipped password, Apple Pay naming, failing target spacing, full and recoverable focus obscuration, blocked payment | Not evaluated | 8 of 8 core decisions matched |

The candidate explicitly distinguished supplied source evidence from runtime observations and
kept untested states separate. In the small-text case, the base called the contrast failure
Critical under its blanket accessibility rule; the candidate used High under the impact rubric.
The added cases selected the appropriate reflow dimension, flagged a shipped password while
preserving autofill, rejected insufficient target spacing and unrecoverable entirely obscured focus,
permitted the user-opened overlay recovery exception, and
separated a branding mismatch from an established blocked payment task.

These are illustrative decision probes, not deterministic runtime tests, proof of general
accuracy improvement, WCAG certification, or a live-site audit. The equal baseline/candidate
results on the shared eight cases do not establish an accuracy gain. The eight added cases
were evaluated after the initial review; they were not used for a baseline comparison.
