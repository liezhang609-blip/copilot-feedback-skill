# Roadmap

`copilot-feedback` v0.1 is a working public draft. The next versions should be
based on real usage, not more abstract explanation.

## v0.2 Questions

The next round should answer:

- How does the skill gradually become useful for a new user?
- How many successful interventions should happen before permission upgrades
  from advisory to semi-autonomous to direct order?
- In which task types does it actually reduce "AI stops too early" behavior?
- When does it over-intervene and add unnecessary ceremony?
- What kinds of vague feedback does it translate best?
- What kinds of tasks still need the human to decide?

## First Usage Experiments

Run the skill against several real tasks:

1. Skill improvement:
   - User says the skill output is still not right.
   - Expected behavior: create success/failure samples, quality dimensions, and
     concrete next edits instead of another generic rewrite.

2. AIGC prompt iteration:
   - User says an image/video result is wrong but cannot explain why.
   - Expected behavior: preserve working traits, isolate failure dimensions, and
     generate a negative-feedback block.

3. App or website build:
   - User asks for an end-to-end usable result.
   - Expected behavior: implement, launch/open, verify, fix obvious defects, and
     avoid stopping at a plan.

4. CAD/document/data workflow:
   - User is a domain beginner and does not know what samples or schema are
     needed.
   - Expected behavior: explain that samples calibrate the workflow, define a
     schema, request or locate representative samples, and set review checkpoints.

## Evaluation Signals

Good signs:

- The user gives less low-value feedback like "continue" or "still not right".
- The main agent asks fewer unnecessary steering questions.
- The next action becomes more concrete after each checkpoint.
- The task gets closer to a usable artifact, not just more analysis.
- The copilot catches missing samples, missing tests, missing verification, or
  missing negative feedback.

Bad signs:

- The copilot produces generic meta-commentary.
- It triggers on simple tasks.
- It asks the user to decide things the agent can safely do.
- It turns into scolding, motivation, or empty reflection.
- It increases process without improving the artifact.

## Likely v0.2 Edits

- Add clearer autonomy upgrade and downgrade examples.
- Add more real user prompts in Chinese and English.
- Add task-specific checklists for AIGC, skill creation, coding, and data work.
- Add examples of "do not trigger" cases.
- Add a lightweight outcome log template.

## Outcome Log Template

```text
Task:
Original user feedback:
Copilot check triggered? yes/no
Steering order:
Action taken:
Result improved? yes/no/unclear
What should v0.2 change?
```
