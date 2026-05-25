# User Profile Intake

Use this reference when the user is new, gives initial data, asks "我该怎么开始", provides scattered personal details, or the request needs profile, schedule, equipment, constraints, and goal context before program analysis.

## Purpose

Convert messy initial user information into a compact coaching profile. Ask only for missing fields that materially change the next decision.

## Intake priority

| Priority | Field | Why it matters |
|---|---|---|
| 1 | Primary goal and deadline | Determines module: hypertrophy, fat loss, specialization, powerlifting, mixed. |
| 2 | Current training status | New, returning, consistent, stalled, injured, high fatigue. |
| 3 | Weekly availability | Controls split choice and plan complexity. |
| 4 | Equipment and load jumps | Controls exercise selection and progression increments. |
| 5 | Current plan/logs | Best evidence for what to change. |
| 6 | Recovery and pain | Controls volume, intensity, deload, substitutions, safety gate. |
| 7 | Body metrics | Needed for fat loss/recomposition and visual shaping. |
| 8 | Preferences and must-keep movements | Improves adherence without breaking programming logic. |

## Required fields by request type

| Request | Minimum useful fields |
|---|---|
| Build first plan | Goal, weekly days, session length, training age, equipment, pain constraints. |
| Modify current plan | Current split, exercises, sets, reps, load, RPE/RIR, schedule, stated problem. |
| Analyze logs/screenshots | Date range, exercise names, sets/reps/load, body part or goal, recent trend. |
| Fat-loss/recomposition | Weight trend, waist/photos if available, steps/cardio, lifting plan, sleep. |
| Specialization | Target muscle, current weekly sets/frequency, target-muscle feel, joint tolerance. |
| Powerlifting/strength | Current SBD/e1RM or recent top sets, RPE accuracy, timeline, sticking points. |

## Profile classification

| Signal | Classification | Programming consequence |
|---|---|---|
| No consistent lifting history | New trainee | Start simple, moderate volume, technique first. |
| Returning after long break | Returning trainee | Use prior experience but lower initial volume/intensity. |
| 3+ months consistent logs | Consistent trainee | Use trend-based adjustments. |
| Performance down, sleep poor, soreness high | Fatigued trainee | Reduce volume/intensity before adding complexity. |
| Pain, numbness, sharp symptoms | Safety flag | Do not prescribe through symptom; advise reduction/evaluation. |
| Clear goal and reliable logs | Data-rich user | Make narrow, evidence-based changes. |
| Vague goal and no logs | Data-sparse user | Give conservative starting plan and ask for 2-4 weeks of logs. |

## Missing data policy

Ask questions only when the missing answer changes the recommendation. Avoid large intake interviews unless the user wants a full setup.

Ask now when missing:

- Training days/session length for any plan construction.
- Equipment for exercise selection.
- Pain/injury when movement safety matters.
- Current plan/logs when the user asks "怎么修改".
- Weight/waist trend when diagnosing fat-loss plateau.
- Current SBD or recent top sets when building powerlifting work.

Do not block the answer when missing:

- Exact body fat percentage.
- Perfect diet details for a training-only request.
- Every exercise preference when a conservative first plan is enough.
- API data if the user already provided usable text/screenshots.

## Input normalization

Normalize user data into this internal structure:

```text
goal:
time_horizon:
profile:
schedule:
equipment:
current_program:
recent_logs:
body_metrics:
recovery:
pain_constraints:
preferences:
unknowns:
assumptions:
```

## Output requirements

When using this reference, include:

- A short profile summary.
- What is known versus assumed.
- The goal module or modules selected.
- Only the missing questions that affect the next step.
- If enough data exists, proceed to recommendation instead of asking more.
