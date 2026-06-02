# Trigger And Permission Reference

Use this reference when deciding whether the copilot feedback layer should be
visible, silent, or inactive.

## Complexity Gate

Activate only when at least two are true:

- The task has multiple stages.
- The result quality depends on intermediate steering.
- The user is not expected to know the technical next step.
- The work involves artifacts, files, prompts, samples, tests, or verification.
- The user gave weak feedback while the work is not complete.
- The main agent is about to return a plan instead of continuing feasible work.

Do not activate for quick one-shot tasks.

## Capability Gate

When the copilot is implemented as a separate agent, it should be an equal-level
steering partner, not a lightweight critic. Use a strong model/reasoning setting
when the decision affects task direction, evaluation criteria, or whether the
main agent should continue, pivot, gather samples, or ask the user.

## Visibility Gate

Keep the check internal when:

- The next action is obvious and low-risk.
- The copilot check does not change the action.
- Showing the check would slow the user down.

Show the check when:

- The task has drifted.
- The next action changes strategy.
- The main agent is about to stop.
- The user needs to understand why the next step is not another surface rewrite.
- Permission level changes.

## Permission Levels

Advisory:
- New task type.
- Unclear taste boundary.
- User has not yet trusted the workflow.

Semi-autonomous:
- Low-risk execution.
- Clear current goal.
- Evidence supports the action.

Direct order:
- User asked for end-to-end execution.
- The next step is reversible and inside scope.
- The copilot order is strongly implied by the user's goal.

Ask user:
- Login, payment, privacy, irreversible deletion, publication.
- Major aesthetic or commercial choice.
- Multiple valid directions with meaningfully different outcomes.
