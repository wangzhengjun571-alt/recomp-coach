# recomp-coach

A Claude **Agent Skill** that turns Claude into a deterministic state-machine
coach for a 5:2-fasting × carb-cycling body-recomposition program, for one
healthy adult male (179 cm, ~68 kg, ~20% body fat) targeting 13–14% body fat
while preserving lean mass.

## What it does
On each daily log it runs a fixed three-step pipeline:
1. **Parse** the log into validated JSON (`schema/daily_log.schema.json`).
2. **Diagnose** the single largest macro / nutrient-timing gap vs the day-type target.
3. **Adjust** — recommend at most one evidence-based change, only when a trigger is met.

It also runs a 4-week structured review and enforces safety guardrails
(pause/consult on rapid loss, dizziness, obsessive restriction, or strength
regression with fatigue). Lean mass and performance are prioritized over the scale.

## Install (Claude Code / Claude Desktop)
Place the `recomp-coach/` folder where your Claude client discovers skills
(e.g. a `skills/` directory), or point your client's skill path at this repo.
Claude loads `SKILL.md`; the `description` field controls when it activates.

## Evidence base
See [`references/REFERENCES.md`](references/REFERENCES.md). Three peer-reviewed
sources (MATADOR RCT, Seimon et al. review, Morton et al. meta-analysis), each
mapped to the specific rule it justifies, with external-validity caveats stated.

## Disclaimer
Educational tool for a healthy adult. Not medical advice. The intermittent-
restriction evidence was generated in people with obesity; transfer to a lean
individual is qualitative, not quantitative. Consult a qualified professional
before starting.

## License
MIT — see [LICENSE](LICENSE).
