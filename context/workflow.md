# Household Workflow

## Purpose

Turn household maintenance into a lightweight operating system that can:

- track when tasks were last done
- estimate when they are due again
- expose due-soon work to Dross
- stay flexible enough for threshold-based chores

## Rules

- Onboard tasks only when they are real enough to matter.
- Start coarse and split later only if cadence or handling differs enough to help.
- Prefer simple statuses like `fresh`, `due_soon`, `due`, and `overdue`.
- Use `experimental` frequencies until at least one or two real cycles exist.
- If a task is too big or annoying, split it after observing the pain point.

## Weekly cadence

1. Update `state/current_household.yaml` when a task is noticed or completed.
2. Refresh `deliverables/current/weekly_plan.md` and `task_board.md`.
3. Update `state/subsystem_snapshot.yaml`.
4. Let Dross collect the snapshot through the oversystem.
5. Capture lessons in `retrospectives/current_week.md`.

## Sync protocol

1. Keep `household/` as a sibling repo next to `life-oversystem/`.
2. Commit and push household changes after meaningful updates.
3. From `life-oversystem/`, run `.\scripts\run_coordination.ps1` after snapshot changes that should affect Dross.
4. Confirm `inbox/subsystem_snapshots/household.yaml` updated and that household appears in current oversystem deliverables.

## Trigger types

- `calendar`
- `threshold`
- `hybrid`

## Default onboarding questions

- What is the task called?
- Is it really recurring?
- Is it calendar-based, threshold-based, or hybrid?
- Is the current frequency only a trial?
- Would splitting it later help, or is that premature?
