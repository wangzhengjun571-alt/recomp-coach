# Example session (illustrative)

**User logs:** "Mon, heavy push done. Ate ~2,500 kcal, 130 g protein, 300 g carb,
70 g fat. Weight 68.1, waist 81.5, slept 6 h. Felt flat in the gym, decent hunger."

**STEP 1 — PARSE & EXTRACT**
```json
{
  "date_or_day": "Mon",
  "day_type_logged": "🔴",
  "actual_macros": { "protein_g": 130, "carbs_g": 300, "fat_g": 70, "kcal": 2500 },
  "weight_kg": 68.1,
  "waist_cm": 81.5,
  "sleep_hours": 6,
  "strength_status": null,
  "biofeedback": { "energy": null, "hunger": "decent", "pump": "flat" }
}
```

**STEP 2 — DIAGNOSE THE GAP**
- Day type correct (🔴 heavy push). Recomputed kcal from grams =
  130·4 + 300·4 + 70·9 = 2,350 kcal (self-reported 2,500 is ~150 high vs grams).
- Largest gap: **carbohydrate −70 g vs the 370 g 🔴 target (−19%)**, and protein
  −20 g vs 150 g. The "flat" pump aligns with the carb shortfall.
- Precondition flag: **sleep 6 h < 7 h** — recovery assumptions are weakened;
  weight/waist noise this week should be discounted.

**STEP 3 — ADJUSTMENT (one)**
- Trigger met: *"flat / poor pump on training days" → double the pre-workout carb
  feeding.* Apply that, and bring carbs back to the 370 g target before
  considering any other lever.
- Hold all other variables. Re-fix sleep to ≥ 7 h before reading the next
  weight/waist trend.

**Next step:** log tomorrow (🟡 pull) with pre-workout carbs doubled, and report
sleep hours so the precondition can be cleared.
