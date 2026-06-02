# Copilot Feedback

Personal Codex skill for complex-task steering.

It acts as a periodic copilot feedback layer: when a task is complex and the
user's feedback becomes vague or the main agent is tempted to stop early, it
translates the user's goal into the next concrete steering order.

Core ideas:

- Use only for complex tasks, not simple one-shot requests.
- Use equal-level reasoning when the copilot runs as a subagent.
- Treat missing negative-feedback ports as a design problem: compile vague
  dissatisfaction into concrete negative feedback and a next steering order.
- Treat vague user feedback as a signal to generate useful negative feedback.
- Preserve positive feedback explicitly.
- Prefer evidence: samples, tests, screenshots, files, outputs, and memory.
- Increase autonomy gradually, from advisory to semi-autonomous to direct order.
- Stop for login, payment, privacy, irreversible actions, and major subjective
  decisions.

Primary file: `SKILL.md`
