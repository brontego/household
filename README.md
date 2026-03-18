# Household

This repository is a Codex-assisted household management system, not a traditional app.

Canonical system name: `Household`

The purpose of this repo is to make recurring home tasks visible, schedulable, and easier for Dross to coordinate with the rest of life.

## Repo layout

```text
household/
  context/
    workflow.md
    task_model.md
  deliverables/current/
    weekly_plan.md
    task_board.md
    change_log.md
  memory/
    notes.md
  retrospectives/
    current_week.md
  state/
    current_household.yaml
    current_week.yaml
    subsystem_snapshot.yaml
  .gitignore
  README.md
```

## Core operating idea

- onboard tasks incrementally as they are noticed
- start coarse, split later only if cadence or handling really differs
- support `calendar`, `threshold`, and `hybrid` triggers
- treat the snapshot as the contract with Dross

Current first tracked task:

- `laundry_daily_wear`

## How to use the system

1. Add or update live task facts in `state/current_household.yaml`.
2. Refresh `deliverables/current/weekly_plan.md` and `deliverables/current/task_board.md`.
3. Update `state/subsystem_snapshot.yaml` so Dross can see current household pressure.
4. When the plan changes mid-week, append the change to `deliverables/current/change_log.md`.
5. At the end of the week, capture lessons in `retrospectives/current_week.md`.

## Trigger types

- `calendar`: do after roughly `N` days
- `threshold`: do when some state is true, like `hamper mostly full`
- `hybrid`: whichever happens first

Laundry is currently modeled as `hybrid`.

## Cross-computer sync

The intended sync model is the same as the other systems:

1. Keep this repo under the same sibling `Github/` folder as `life-oversystem`, `mealplanning`, `budgeting`, `fitness`, and `axiom`.
2. Commit and push this repo after meaningful updates.
3. On another computer, clone or fast-forward it with the same workspace bootstrap flow used for the other repos.

Expected remote once created:

```text
https://github.com/brontego/household.git
```

## First-time repo setup

If this folder is not a git repo yet:

```powershell
git init -b main
git add -A
git commit -m "Build household management system workspace"
git remote add origin https://github.com/brontego/household.git
```

If the GitHub repo does not exist yet, create an empty private repo named `household` under `brontego`, then run:

```powershell
git push -u origin main
```

## Cross-computer setup

The reliable setup flow on another computer is:

1. clone `life-oversystem`
2. run `.\life-oversystem\scripts\bootstrap_workspace.ps1 -Owner brontego -SyncExisting`
3. open `life-systems.code-workspace`

This works because `bootstrap_workspace.ps1` is wired to clone or sync `household` alongside the other sibling repos.

## Verify cross-computer sync

After bootstrapping on another computer, verify:

- `Github/household/README.md` exists
- `Github/household/state/subsystem_snapshot.yaml` exists
- `Github/life-systems.code-workspace` includes `Household`
- `git -C household remote -v` shows `https://github.com/brontego/household.git`

## Dross sync contract

Dross does not deep-read this repo by default. Dross reads:

- `state/subsystem_snapshot.yaml`

Then `life-oversystem/scripts/collect_snapshots.py` copies that snapshot into:

- `life-oversystem/inbox/subsystem_snapshots/household.yaml`

After that, oversystem coordination can include household work in:

- `deliverables/current/weekly_coordination_plan.md`
- `deliverables/current/week_at_a_glance.md`
- `deliverables/current/risk_watchlist.md`

## Verify Dross sync

From `life-oversystem/`, run:

```powershell
.\scripts\run_coordination.ps1
```

Then verify:

- `life-oversystem/inbox/subsystem_snapshots/household.yaml` exists
- `life-oversystem/deliverables/current/weekly_coordination_plan.md` includes `household`
- `life-oversystem/deliverables/current/week_at_a_glance.md` shows household items on relevant days

## New-computer setup

Once the remote exists, the intended new-computer flow is:

1. clone `life-oversystem`
2. run `life-oversystem/scripts/bootstrap_workspace.ps1`
3. open `life-systems.code-workspace`

That bootstrap flow is being wired to include `household` alongside the other repos.

## Current startup bias

- one real task is better than a giant theoretical task registry
- due-soon is enough; precision can come later
- task splitting should be earned by repeated annoyance, not guessed upfront
