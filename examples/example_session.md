# Example session (illustrative — generic user)

## 0. First-time setup

**User says:** "设定资料：男，179 cm，68 kg，体脂 20%，目标 14%，28 岁"

**Coach computes and displays the personalized plan:**

```
BMR = 10×68 + 6.25×179 − 5×28 + 5 = 1,664 kcal
LBM = 68 × (1 − 20/100) = 54.4 kg
Training TDEE = 1,664 × 1.65 ≈ 2,745 kcal
Rest TDEE     = 1,664 × 1.2  ≈ 1,997 kcal

🔴 HIGH-CARB:
  kcal = 2,745 + 150 = 2,900
  protein = 68 × 2.2 = 150 g
  fat = 68 × 0.9 = 60 g
  carb = (2,900 − 600 − 540) / 4 = 440 → 440 g

🟡 MODERATE-CARB:
  kcal = 2,745 − 250 = 2,495 → 2,500
  protein = 68 × 2.2 = 150 g
  fat = 68 × 1.0 = 68 → 70 g
  carb = (2,500 − 600 − 630) / 4 = 318 → 320 g

🟢 FAST:
  kcal = max(1,664×0.35, 87×4+150) = max(582, 498) = 600
  protein = 54.4 × 1.6 = 87 → 90 g
  fat = 68 × 0.25 = 17 → 20 g
  carb = (600 − 360 − 180) / 4 = 15 → 15 g

Weekly deficit ≈ 2,980 kcal → theoretical fat loss ≈ 0.39 kg/week ✅
```

---

## 1. Daily log

**User logs:** "周一，大重量推胸练完了。吃了 ~2,500 kcal，130 g 蛋白，300 g 碳水，
70 g 脂肪。体重 68.1，腰围 81.5，睡了 6 小时。训练时 pump 感觉不好，有点饿。"

**STEP 1 — PARSE & EXTRACT**
```json
{
  "date_or_day": "周一(Mon)",
  "day_type_logged": "🔴",
  "actual_macros": { "protein_g": 130, "carbs_g": 300, "fat_g": 70, "kcal": 2500 },
  "weight_kg": 68.1,
  "waist_cm": 81.5,
  "sleep_hours": 6,
  "strength_status": null,
  "biofeedback": { "energy": null, "hunger": "有点饿", "pump": "不好/flat" }
}
```

**STEP 2 — DIAGNOSE THE GAP**
- Day type correct (🔴 heavy push). Recomputed kcal from grams =
  130×4 + 300×4 + 70×9 = 2,350 kcal (self-reported 2,500 is ~150 kcal high vs
  grams — using 2,350 for analysis).
- Largest gap: **碳水 −140 g vs 🔴 目标 440 g (−32%)**，蛋白质 −20 g vs 150 g。
  Pump 差与碳水缺口吻合。
- 睡眠前提条件未满足：**6 h < 7 h** — 本周体重/腰围数据噪声增大，恢复假设不成立。

**STEP 3 — ADJUSTMENT (one)**
- 触发条件满足：*"Flat / poor pump on training days" → 训练前碳水翻倍。*
  同时将总碳水拉回 440 g 目标。
- 其他变量不变。先修睡眠到 ≥ 7 h，再读下周趋势。

**下一步：** 明天 🟡 拉类训练，训练前碳水翻倍，报告睡眠时长。
