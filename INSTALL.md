# Install

## Codex

From this repository root:

```powershell
Copy-Item -Recurse .\skills\copilot-feedback "$env:USERPROFILE\.codex\skills\copilot-feedback"
```

Restart Codex after copying.

## Manual Install

Copy this folder:

```text
skills/copilot-feedback
```

to your local skills directory.

The required file is:

```text
SKILL.md
```

The `references/` and `evals/` folders are optional but recommended.

## Verify

After restart, try a complex-task prompt such as:

```text
I am improving an AI image prompt workflow. The output is still not right, but I cannot explain why. Help me keep going until the workflow improves.
```

The skill should avoid empty reflection and produce a concrete copilot check with positive feedback, negative feedback, and a steering order.
