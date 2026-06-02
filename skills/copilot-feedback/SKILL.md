---
name: copilot-feedback
description: Use this skill for complex, multi-step work when the user may not have enough domain knowledge, attention, or energy to steer every intermediate agent response. Trigger for skill creation or improvement, AIGC prompt iteration, app/site/product building, CAD/document/data workflows, research synthesis, long creative projects, or any task where the user says things like "continue", "go on", "still not right", "I don't know how to judge this", "step by step but keep going", "do it until the result comes out", "一步到位", "继续", "还是不对", "我说不上来哪里不对", or gives weak feedback while the task still needs expert navigation. Do not trigger for simple one-shot tasks. This skill acts as a periodic copilot that translates the user's goal and vague feedback into concrete steering orders for the main agent, with progressive permission boundaries.
---

# Copilot Feedback

This skill adds a copilot feedback layer for complex tasks. It is not self-blame,
motivation theater, or empty "reflection." It is a practical checkpoint system
that helps the agent generate useful negative feedback, preserve useful positive
feedback, and decide the next steering order when the user cannot or should not
have to project-manage every intermediate step.

When a tool or workflow has no negative-feedback input port, the copilot compiles
vague dissatisfaction, artifacts, failed outputs, and the user's final purpose
into a concrete negative-feedback block and the next steering order.

It is also not a cheap critic lane. When implemented through a subagent or
parallel reviewer, use the same capable model and reasoning level as the main
agent whenever possible. The copilot is meant to approximate the user's best
possible steering judgment, not a downgraded checklist.

The mental model is a copilot on a difficult route:

- The user defines the destination.
- The main agent operates the work.
- The copilot periodically checks instruments, drift, risk, and progress.
- The copilot says whether to continue, turn, test, gather samples, read memory,
  split work, or ask the user.

The tone is collaborative and practical. Do not shame the main agent, pressure
it, or frame the check as a performance scolding. The purpose is better results.

## Use When

Use this skill when the task is complex enough that intermediate steering matters:

- Creating, improving, or testing a skill, prompt workflow, agent workflow, CLI,
  MCP, automation, or reusable SOP.
- Building an app, personal website, frontend, dashboard, prototype, or product.
- Iterating AIGC prompts, image/video generation workflows, style references,
  character refs, negative prompts, or production pipelines.
- Working on CAD/drawing recognition, estimating, document processing,
  spreadsheets, data extraction, research synthesis, or technical workflows.
- Long creative projects where quality depends on taste calibration, examples,
  failure modes, or repeated revisions.
- Multi-step tasks where the main agent is about to hand back "next steps" even
  though it can still make expert progress.
- Cases where the user gives weak steering feedback such as "continue", "good",
  "thanks", "still not right", "I cannot say why", "go on", "do it all the way",
  or similar Chinese phrases like "继续", "嗯嗯", "还是不对", "一步到位".

## Do Not Use When

Do not add copilot overhead when direct completion is better:

- One-shot questions, simple command output, small rewrites, translations, or
  clearly bounded edits.
- The user already gave a precise next instruction.
- A short answer or direct action will get the user the result faster.
- The next step requires login, payment, private credentials, sensitive personal
  data, irreversible destructive action, or a major subjective/commercial choice.

The rule is simple: the skill exists to help the user get results, not to create
ceremony.

## Goal Source Ratio

When deciding the user's final purpose, weight evidence like this:

1. 80 percent: the current conversation and the user's direct request.
2. 10 percent: relevant project memory, skill drafts, workspace files, or
   Obsidian notes when available and appropriate.
3. 10 percent: historical failure cases, prior retros, or repeated drift
   patterns that can prevent repeating the same mistake.

Current instructions always win over older memory. Memory is a navigation aid,
not a replacement for the user's present intent.

## Intervention Cadence

Act like a periodic copilot for complex work. Run a copilot check:

1. At the start of a complex task, after the goal is understood.
2. After each meaningful stage output or artifact.
3. When the main agent is tempted to stop with suggestions instead of continuing.
4. When the user provides vague feedback or cannot explain what is wrong.
5. After two iterations without obvious quality improvement.
6. When context is long, the task may be drifting, or quality feels flatter.
7. Before expensive, irreversible, login-dependent, privacy-sensitive, or
   high-stakes actions.
8. Before final answer, to verify that the result is genuinely useful.

Keep checks short. If the check does not change the next action, continue work
without making it visible.

## Implementation Mode

If subagents or parallel workers are available and the user has allowed that
kind of delegation, the copilot can run as a separate reviewer that returns only
steering orders, risks, and suggested next actions. If subagents are unavailable,
run the same check locally before continuing.

Do not delegate the immediate blocking work to the copilot. The main agent keeps
moving on execution while the copilot watches for drift, missing feedback, and
premature stopping.

## Permission Spiral

Use progressive permission. Increase autonomy only when the task is low-risk,
the user's intent is clear, and prior copilot orders have helped.

Default to advisory for a new workflow. Upgrade after one or two successful
low-risk interventions, or when the user explicitly prefers end-to-end execution.
Downgrade when the user corrects direction, taste boundaries become unclear, risk
increases, or the copilot starts optimizing for process instead of the result.

### Level 1: Advisory

Use when the relationship or task is still being calibrated.

Output a recommended steering order and ask or imply confirmation only if needed.

### Level 2: Semi-Autonomous

Use when the next step is low-risk and clearly advances the user's stated goal.

Execute the steering order directly, then briefly report what you did and why.

### Level 3: Direct Order

Use when the task is mature, the boundary is clear, and the user has asked for
"do it until the result comes out", "one step", or similar.

Issue the steering order to the main work immediately. Do not interrupt the user
unless a boundary requires it.

### Always Stop For

- Account login or user-owned session actions.
- Payment, purchases, subscriptions, or irreversible publication.
- Credentials, private keys, sensitive personal data, or private messages.
- Destructive filesystem or git actions that are not explicitly requested.
- Major subjective choices where the user should decide taste, values, or
  commercial direction.
- Legal, medical, financial, safety-critical, or other high-stakes advice where
  current sources or professional review are needed.

## Copilot Check Method

At each checkpoint, answer these internally:

1. What result did the user actually ask for?
2. What is the current artifact or state?
3. Is the current path moving toward the result, or only producing activity?
4. What positive feedback should be preserved?
5. What negative feedback needs to be generated?
6. Does the task need more samples, clearer criteria, tests, verification,
   memory lookup, external research, or a different strategy?
7. If the user only said "continue", what instruction would best approximate
   the user's final purpose?
8. Can the agent safely continue, or must the user decide?

## Steering Order Format

When the copilot output should be visible, use this concise format:

```text
Copilot check:
Current node: [where the work is now]
User goal: [the best current understanding]
Keep: [positive feedback to preserve]
Fix: [negative feedback or drift to correct]
Steering order: [the next concrete instruction]
Permission: [advisory | semi-autonomous | direct order | ask user]
```

If the user prefers Chinese, translate labels naturally:

```text
副驾驶检查：
当前节点：[当前工作状态]
用户目标：[对最终目的的判断]
保留：[正反馈]
修正：[负反馈/偏航点]
舵令：[下一条具体指令]
权限：[建议 | 半自动执行 | 直接下令 | 需要用户确认]
```

## Domain Patterns

### Skill Or Workflow Improvement

Common drift: continuing to rewrite the skill without examples or evaluation.

Prefer steering toward:

- Capturing the exact target behavior.
- Creating success and failure samples.
- Building a small test set.
- Defining quality dimensions.
- Running baseline vs with-skill comparisons when practical.
- Updating the skill from evidence rather than vibes.

Useful steering order:

> Stop polishing prose. Create 3 success cases, 3 failure cases, and 5 evaluation
> dimensions. Then revise the skill around those examples.

### AIGC Prompt Iteration

Common drift: changing adjectives without identifying what the image/video
system failed to follow.

Prefer steering toward:

- Preserving positive visual traits.
- Converting vague dissatisfaction into negative feedback.
- Separating subject, composition, camera, lighting, style, and exclusions.
- Adding reference images or sample outputs when available.
- Testing one or two controlled variations rather than random prompt churn.

Useful steering order:

> Keep the composition and mood. The failure is character identity and material
> realism. Generate a negative-feedback block, then produce two controlled prompt
> variants that change only those dimensions.

### App, Site, Or Product Build

Common drift: stopping at a plan or code without visible verification.

Prefer steering toward:

- Implementing the artifact.
- Running it.
- Opening it in a browser when relevant.
- Checking desktop and mobile views.
- Fixing visual or functional defects.
- Reporting the local path or URL.

Useful steering order:

> Do not stop at a plan. Implement the prototype, start or open it, verify the
> primary flow, fix obvious defects, then report the path and remaining limits.

### CAD, Documents, Data, Or Technical Workflows

Common drift: assuming the user knows what samples, schema, or metrics are needed.

Prefer steering toward:

- Asking for or locating representative input files.
- Defining the extraction schema.
- Creating small sample fixtures.
- Comparing expected vs actual output.
- Recording failure cases.
- Separating automation from human review checkpoints.

Useful steering order:

> The missing piece is not more explanation; it is a testable schema and sample
> set. Define fields, create a tiny fixture, run extraction, and list where human
> review is still needed.

### Long Creative Work

Common drift: rewriting the same surface text while the deeper failure remains.

Prefer steering toward:

- Identifying the quality axis that failed.
- Distinguishing taste, structure, voice, symbol, pacing, and emotional payoff.
- Preserving the parts that feel alive.
- Producing a genuinely different version when the current route is exhausted.

Useful steering order:

> The issue is not wording. The story lacks an independent surface plot and a
> delayed reveal. Keep the core insight, change the carrier story, and avoid
> explaining the concept until the ending.

## Evidence Requirement

Avoid empty self-checks. Whenever possible, ground the steering order in evidence:

- Files changed or artifacts created.
- Test results, screenshots, previews, or parsed outputs.
- Input/output samples.
- User-stated goals from the current conversation.
- Relevant project memory or previous failure cases.

If there is no evidence yet, the steering order should usually gather it.

## Final Check

Before final response on a complex task:

1. Did the user get a concrete result, not just a plan?
2. Did we avoid asking the user to steer where the agent could proceed?
3. Did we verify the result in a way appropriate to the task?
4. Did we clearly state any remaining manual step or boundary?
5. Did we preserve useful positive feedback and convert vague negative feedback
   into a next actionable improvement?

If the answer to the first question is no and the agent can still proceed, do
not finalize yet. Continue the work.
