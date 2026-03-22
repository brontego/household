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

## Method for now

Use low-management automation only where the system already has enough information to be honest.

- Derive `fresh`, `due_soon`, `due`, and `overdue` from `last_done + target_frequency_days` for `calendar` and `hybrid` tasks.
- Derive a rough `next_due_estimate` when a task has both a real completion date and a usable cadence.
- Build the weekly candidate list from task status, effort, and any live `current_signal`.
- Carry unfinished due tasks forward until they are completed or consciously rescoped.
- After one to two real cycles, prompt a cadence review instead of assuming the first frequency guess was right.
- When other systems are heavy, prefer one low-to-medium household task instead of stacking several medium tasks.
- For threshold chores with backlog potential, use a simple manual severity read instead of a complex tracker:
  one waiting cycle is normal due pressure, repeated cycles without clearing the task means the task has started to sprawl.

Do not fake precision for threshold tasks. Trash fullness, hamper fullness, and similar signals still need a manual reality check.

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
- What can be honestly derived automatically, and what still needs a manual reality check?
