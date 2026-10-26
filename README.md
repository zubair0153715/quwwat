# Quwwat — Free Strength-Training Planner

**Live:** https://clinic-demo.fastapicloud.dev/quwwat

Original clean-room build from the daily-app-gap-build series (2026-10-26).
Target studied from PUBLIC sources only: Fitbod — a $15.99/mo ($95.99/yr)
AI strength-training app with 15M+ downloads and a 4.8★ iOS rating, whose
biggest gaps are: no free version at all (trial = 3 workouts, card up
front), no injury filter, and no full periodized training blocks.

## What Quwwat does differently

1. **Free, unlimited, no account, no card, no trial clock.** The whole
   planner runs in the browser; plans save to the user's own device.
2. **Injury filter first, not an afterthought.** Tick shoulder / elbow /
   wrist / knee / lower back and every exercise loading that joint is
   removed from the plan — the exact feature Fitbod lacks.
3. **A real 4-week periodized block, not session-by-session drift.**
   Documented set × rep × % tables per goal (strength / muscle / general)
   with a deload week 4 — the full block Fitbod doesn't ship.
4. **Honest loads.** Weights are prescribed only from a 1RM the user
   actually enters (Epley formula, shown with its maths); everything else
   gets sets × reps + an RPE target and a "2 reps in reserve" rule —
   never a made-up number on day one.
5. **Muscle recovery map from the plan itself.** Every muscle shows
   trained / recovering (<48h) / ready (≥48h) across the generated week.
6. **Home-first equipment profiles.** Full gym, dumbbells-only, or
   bodyweight-only — no gym membership assumed.
7. **Honest scope, stated on the page.** General fitness information, not
   medical advice; stop on sharp pain and see a clinician; no nutrition,
   no cardio, no form videos — listed as not-included, not upsold.

## AI feature

Optional Gemini coaching notes on a generated plan (form cues + why this
split + how to progress). The key is read from the environment at call
time only and is never stored; the full planner works without it.

## Verify

```
python3 tests/verify.py
```

41 checks: Epley maths hand-verified (100 kg × 5 = 116.67 kg 1RM),
plate rounding, block tables, injury/equipment/level filters, session
coverage, 1RM-driven loads, determinism, the 48h recovery rule, and
route smoke tests. No network, no key needed.
