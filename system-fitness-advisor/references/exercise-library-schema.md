# Exercise Library Schema

Use `data/exercise-library.json` as the structured exercise source for plan construction, exercise substitution, and exercise rotation.

## Current source

The first library import came from user-provided exercise-library text. A second import added clear exercise names visible in user-provided app screenshots.

Current coverage:

- Total exercises: 147
- Body parts: 胸, 背, 肩, 腿, 二头, 三头, 臀部, 腹部
- Equipment groups: 杠铃, 哑铃, 绳索, 悍马机, 史密斯, 史密斯机, 器械, 自重, 壶铃

## JSON shape

Top-level fields:

- `schema_version`: schema version string.
- `source_file`: original source path for the import.
- `exercise_count`: number of exercise entries.
- `body_parts`: source body-part groups.
- `fields`: field descriptions.
- `exercises`: exercise records.

Exercise record fields:

- `id`: stable generated identifier, using body part, equipment, and source order.
- `name_zh`: Chinese exercise name.
- `body_part`: original body-part group.
- `body_part_id`: normalized English body-part id.
- `equipment`: original equipment group.
- `equipment_id`: normalized English equipment id.
- `primary_muscles`: inferred primary muscles; refine manually when precision matters.
- `movement_pattern`: inferred movement pattern used for programming.
- `goals`: default applicable goals.
- `source`: source file label.
- `notes`: free-form correction or coaching notes.

## Update rules

- Preserve existing `id` values when editing an exercise.
- Add new exercises at the end of the relevant body-part group unless a full reimport is intended.
- When importing from screenshots, add only clearly readable names; skip partially hidden or uncertain cards.
- When the user requests an exercise that is not in the library, do not add it silently. Ask for confirmation when the exercise is likely to recur.
- Mark user-confirmed additions with `source: "user_requested"` or `source: "user_correction"` and include the user-facing reason in `notes`.
- Prefer correcting `primary_muscles`, `movement_pattern`, `goals`, and `notes` over deleting source exercises.
- If an exercise name appears in multiple body parts, keep separate records and distinguish by `body_part` and `movement_pattern`.
- Treat inferred fields as defaults, not final truth. The user's corrections override inferred metadata.

## Selection rules

When selecting exercises:

1. Filter by target `body_part` or `primary_muscles`.
2. Filter by available `equipment`.
3. Match `movement_pattern` to the program slot.
4. Match `goals` to the training goal.
5. Prefer familiar exercises from the user's logs when available.
6. Use substitutions from the same body part, movement pattern, and equipment class first.

## Missing exercise fallback

When a requested exercise is absent:

1. Try synonym and near-name matching.
2. Search by the intended `body_part`, `equipment`, and `movement_pattern`.
3. Offer the closest in-library substitution first.
4. If no in-library option fits, use the outside-library exercise temporarily and say it is outside `data/exercise-library.json`.
5. Ask whether to add it to the library if the user plans to use it regularly.

Never present an outside-library exercise as if it already exists in the library.
