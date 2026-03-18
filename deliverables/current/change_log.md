# Household Change Log

Purpose: capture plan deltas so the module can stay lightweight without silently rewriting itself.

## Entry template

```yaml
date:
changed_by:
trigger:
previous_plan:
new_plan:
why_now:
expected_risk:
what_to_monitor_next_7_days:
follow_up_result:
```

## Current week entries

```yaml
date: 2026-03-18
changed_by: Codex
trigger: user_committed_to_doing_laundry_today_but_not_to_folding
previous_plan: due_soon_laundry_with_a_thursday_or_friday_window_and_an_implicit_saturday_fold_suggestion
new_plan: due_laundry_today_with_completion_defined_as_wash_plus_dry_or_hang_and_folding_left_unplanned
why_now: the_real_household_decision_for_today_is_clear_and_should_be_reflected_without_sneaking_extra_scope_back_in
expected_risk: folding_could_still_float_back_in_as_guilt_if_the_completion_definition_is_not_respected
what_to_monitor_next_7_days: whether_seven_days_felt_right_and_whether_folding_needs_its_own_task
follow_up_result:
```
