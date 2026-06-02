# Steering Order Examples

## Skill Draft Is Stalling

```text
Copilot check:
Current node: The skill has been rewritten twice but still lacks sharper output.
User goal: A reusable skill that reliably improves complex allegory writing.
Keep: The user wants layered stories, delayed insight, and strong retellability.
Fix: The workflow still lacks success/failure samples and quality dimensions.
Steering order: Stop writing another story. Build a sample table with 5 good
examples, 5 bad examples, and 6 quality dimensions, then revise the skill.
Permission: semi-autonomous
```

## AIGC Prompt Has No Negative Feedback Port

```text
Copilot check:
Current node: The image prompt produced a decent mood but wrong character feel.
User goal: A visual result that keeps the atmosphere but removes the AI-like face.
Keep: Composition, lighting, and emotional tone.
Fix: Identity, skin texture, and costume material realism.
Steering order: Create a negative-feedback block for identity and material
failure, then generate two controlled prompt variants that preserve composition.
Permission: direct order
```

## Product Build Wants To Stop At Plan

```text
Copilot check:
Current node: The agent has a product plan but no visible prototype.
User goal: A usable first-screen app prototype.
Keep: The three primary use cases and low-cost MVP boundary.
Fix: No user-visible artifact has been created or verified.
Steering order: Implement the static prototype, open it locally, verify the main
flow at desktop and mobile widths, then report the path.
Permission: direct order
```

## CAD Or Data Workflow Needs Samples

```text
Copilot check:
Current node: The workflow concept exists but has no testable input/output.
User goal: A practical drawing-recognition or estimating workflow.
Keep: The desire for automation with human review checkpoints.
Fix: The schema, representative samples, and error metrics are missing.
Steering order: Define the extraction fields, request or locate 2 sample drawings,
create expected outputs, then test extraction against them.
Permission: advisory if samples require the user; semi-autonomous otherwise
```
