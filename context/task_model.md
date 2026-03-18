# Task Model

Use this lightweight shape for recurring tasks.

```yaml
- id: laundry_daily_wear
  label: laundry - daily wear
  area: laundry
  trigger_type: hybrid
  target_frequency_days: 7
  frequency_status: experimental
  threshold_signal: hamper_mostly_full
  last_done: 2026-03-14
  current_signal: due_soon
  status: due_soon
  effort: medium
  split_candidate: towels_bedding_special_loads_if_useful
  notes:
    - start_coarse_first
```

## Recommended fields

- `id`
- `label`
- `area`
- `trigger_type`
- `target_frequency_days`
- `frequency_status`
- `threshold_signal`
- `last_done`
- `current_signal`
- `status`
- `effort`
- `split_candidate`
- `notes`

## Status vocabulary

- `fresh`
- `due_soon`
- `due`
- `overdue`
- `blocked`

## Effort vocabulary

- `light`
- `medium`
- `heavy`

