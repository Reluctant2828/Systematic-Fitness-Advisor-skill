# Nutrition Log Analysis

Use this reference when the user provides diet records, meal logs, calories, macros, protein intake, hunger, adherence, or asks how diet should support hypertrophy, fat loss, recomposition, specialization, strength, or powerlifting.

Do not use this skill for nutrition-only lookup when there is no training or body-composition decision.

## Purpose

Turn nutrition logs into training-relevant decisions without pretending to be a medical dietitian or exact food database.

## Supported inputs

- Text meal logs.
- CSV, JSON, spreadsheet, or app export with calories/macros.
- Screenshots of food logs or calorie dashboards.
- User estimates for calories, protein, carbs, fat, fiber, water, sodium, hunger, and adherence.

Useful fields:

```text
date:
meal:
food:
quantity:
calories:
protein_g:
carbs_g:
fat_g:
fiber_g:
water_ml:
hunger:
adherence:
notes:
```

## Script support

Use `scripts/manage_user_data.py import-nutrition` to save nutrition records into `nutrition-history.json`. Use `scripts/manage_user_data.py summary` for daily averages and recent totals.

## Reliability

| Evidence | Use |
|---|---|
| 7-14 days of logged calories and protein | Useful for cut, bulk, and recomposition adjustments |
| Protein only | Useful for muscle retention and recovery checks |
| Calories without bodyweight trend | Context only; do not over-adjust |
| Bodyweight trend without intake | Use body metrics first, infer diet cautiously |
| Screenshot food logs | Extract but mark uncertainty |

## Decision rules

| Pattern | Likely interpretation | Training-relevant action |
|---|---|---|
| Protein low during cut | Higher muscle-loss and hunger risk | Raise protein target before adding training stress |
| Calories very low and performance falling | Deficit too aggressive or fatigue too high | Reduce cardio/volume or increase intake slightly |
| Calories stable, weight and waist falling, performance stable | Productive cut | Keep plan |
| Calories high, waist rising fast, strength not improving | Surplus may be too high | Reduce surplus or improve adherence |
| Inconsistent weekdays/weekends | Adherence issue | Use weekly average, not single-day correction |
| Carbs very low around hard sessions | Performance support issue | Place carbs around key training when appropriate |

## Macro guidance

Use ranges and context, not rigid prescriptions:

- Protein: usually anchor first for fat loss/recomposition and hypertrophy support.
- Calories: interpret against weight, waist, photos, performance, hunger, and adherence.
- Carbs: support high-volume hypertrophy, hard leg days, and powerlifting intensity.
- Fats: avoid pushing extremely low; do not make medical claims.
- Fiber and hydration: use as adherence and hunger context.

## Output requirements

Include:

- Data range and confidence.
- Daily or weekly calorie/protein averages when available.
- Relationship to training performance and body metrics.
- The smallest nutrition change for the next 1-2 weeks.
- What to track next: calories, protein, weight average, waist, performance, hunger, steps, sleep.
