# Copilot Feedback Skill

> A same-intelligence copilot for complex AI tasks. It turns vague human feedback into concrete steering orders.

很多 AI 新手不是不想继续，也不是故意给不出反馈，而是卡在一个很真实的位置：

- AI 给了阶段性结果，但还没到最终结果。
- 人类用户不是程序员、设计师、prompt 工程师或评测专家。
- 用户只能说“继续”“还是不对”“我说不上来哪里不对”。
- AI 于是停下来问用户下一步怎么做，或者给一串建议，然后任务断掉。

`copilot-feedback` 就是为这个节点设计的。

它不是 PUA skill，也不是让 AI 写检讨式“反思”。它更像复杂任务里的副驾驶：周期性看仪表盘、看航线、看偏航风险，把用户模糊的感受编译成主 agent 下一步应该执行的舵令。

## One-Line Definition

When the user cannot provide expert intermediate feedback, this skill acts as a copilot feedback layer that preserves useful positive feedback, generates practical negative feedback, and issues the next concrete steering order.

## Why It Exists

Modern AI is powerful enough to build apps, websites, skills, AIGC workflows, research pipelines, and technical tools end to end. But many workflows still fail for a simple reason:

> The AI expects the user to act like a professional project manager at every intermediate checkpoint.

Most users do not know what to ask next. They know the destination, but not the next steering command.

This skill fills that gap.

## The Missing Negative-Feedback Port

Some tools, especially image and video generation tools, have no clean negative-feedback input. The user sees an output and feels it is wrong, but the system only accepts another prompt.

`copilot-feedback` treats that as a design problem:

1. Keep what worked.
2. Identify what failed.
3. Translate vague dissatisfaction into a concrete negative-feedback block.
4. Decide whether to continue, pivot, gather samples, test, or ask the user.

Example:

```text
Copilot check:
Current node: The image prompt produced a decent mood but wrong character feel.
User goal: Keep the atmosphere while removing the AI-like face.
Keep: Composition, lighting, emotional tone.
Fix: Identity, skin texture, costume material realism.
Steering order: Create a negative-feedback block for identity and material failure, then generate two controlled prompt variants that preserve composition.
Permission: direct order
```

## What It Does

- Acts as a periodic copilot during complex tasks.
- Helps when the user gives weak feedback like “continue”, “still not right”, “go on”, “继续”, “还是不对”, or “我说不上来哪里不对”.
- Translates user intent into concrete next instructions.
- Prevents the main agent from stopping too early with only suggestions.
- Uses positive feedback and negative feedback instead of empty self-reflection.
- Encourages evidence: samples, tests, screenshots, files, expected outputs, and failure cases.
- Gradually increases autonomy as trust improves.

## What It Is Not

- Not a motivation hack.
- Not an AI scolding prompt.
- Not a “work harder” wrapper.
- Not useful for every tiny task.
- Not a replacement for user judgment on login, payment, privacy, irreversible actions, or major taste decisions.

## When To Use It

Use it for complex, multi-step work:

- Skill creation or improvement.
- AIGC prompt iteration.
- Image/video production workflows.
- App, website, frontend, dashboard, or prototype building.
- CAD drawing recognition or estimating workflows.
- Document, spreadsheet, data, or research pipelines.
- Long creative projects where quality depends on repeated calibration.

Do not use it for simple one-shot tasks.

## The 80/10/10 Goal Rule

When deciding the user's true destination:

- 80% comes from the current conversation.
- 10% comes from relevant project memory, drafts, or workspace files.
- 10% comes from historical failure cases and previous drift patterns.

Current instructions always win over old memory.

## Permission Spiral

The copilot does not immediately take over. It climbs gradually:

1. **Advisory**: suggest the steering order.
2. **Semi-autonomous**: execute low-risk next steps and report why.
3. **Direct order**: when intent is clear and the user wants end-to-end progress, steer the main agent without stopping for every micro-decision.

It always stops for login, payment, privacy, irreversible actions, sensitive data, high-stakes advice, or major subjective choices.

## Example Steering Order

```text
副驾驶检查：
当前节点：主 agent 准备继续重写 skill，但质量没有明显提升。
用户目标：做出一个稳定可用的 Allegory Architect skill。
保留：多层寓言、延迟醒悟、可复述的目标。
修正：当前缺少优秀样本、失败样本、评价维度和测试流程。
舵令：不要继续写新故事。先建立 5 个成功样本、5 个失败样本和 6 条质量标准，再重写 skill。
权限：半自动执行。
```

## Install

Copy the skill folder into your Codex skills directory:

```powershell
Copy-Item -Recurse .\skills\copilot-feedback "$env:USERPROFILE\.codex\skills\copilot-feedback"
```

Then restart Codex so the skill list reloads.

For Claude-style skill setups, copy the same folder into your local skills directory if your environment supports `SKILL.md`-based skills.

## Repository Structure

```text
skills/copilot-feedback/
  SKILL.md
  README.md
  references/
    trigger-and-permission.md
    steering-order-examples.md
  evals/
    evals.json
```

## Status

Version: v0.1

This is an early public draft. It was designed from a real discussion about why AI agents often stop at the exact moment a non-expert user needs better steering, not more choices.

Next step: use real tasks to test how quickly the copilot becomes helpful for new users, when permission should upgrade, and where it over-intervenes. See [ROADMAP.md](ROADMAP.md).

## License

MIT
