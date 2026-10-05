# Changes from Proposal

- Reduced dataset from 3,000 to 638 titles (English only) to ensure sufficient annotation coverage.
- Switched from binary interest labels to a 1–6 Likert scale to capture disagreement, per instructor feedback.
- Added clickbait tactic labels (multi-label) as a less subjective dimension, per Dr. Wilson's addendum.
- Adopted hybrid design: 30 common titles (ground truth) + 100 unique titles (coverage).
- 5 annotators × 50 titles = 250 annotations.
- Ground truth from common set (mean of 5 Likert scores), disagreement via variance.
- Evaluation on common set only.
- Dropped full Reddit collection due to RSS rate limiting; used r/all where possible.
- YouTube uses mostPopular (not search) to avoid topic bias.
- Structural and linguistic feature analysis (proposal Section IX) remains for Phase 2.
