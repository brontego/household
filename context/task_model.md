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
  next_due_estimate: 2026-03-21
  split_candidate: towels_bedding_special_loads_if_useful
  current_cycle_plan:
    completion_marker: wash_and_dry_or_hang_done
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
- `current_cycle_plan`
- `split_candidate`
- `notes`

## Optional derived fields

- `next_due_estimate`
- `weekly_candidate`
- `carry_forward`
- `backlog_severity`

These should be derived only when the system has enough real information to support them.

## Automation bias for now

- `calendar` and `hybrid` tasks can derive due status from `last_done + target_frequency_days`
- `threshold` tasks still need a manual reality check
- tasks like folding can use a simple manual backlog severity such as one waiting load vs multiple wash cycles without folding
- unfinished due tasks should carry forward by default
- cadence review should happen after one to two real cycles, not by guess

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
