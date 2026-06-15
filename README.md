# codex-goals-for-a-task

Turn a messy task request into a structured execution brief, a Codex goal draft, and bounded parallel sub-goals.

把模糊任务请求整理成可执行简报、Codex goal 草稿，以及边界清楚的并行子目标。

![From messy task to goal brief](assets/images/01-from-messy-task-to-goal-brief.png)

## What It Does

`codex-goals-for-a-task` is a Codex Skill for planning before execution. It helps Codex translate a user's raw task into:

- a filled execution brief,
- a top-level goal draft,
- concrete success criteria,
- expected deliverables,
- validation steps,
- independent sub-goal prompts for parallel agents.

`codex-goals-for-a-task` 是一个面向 Codex 的规划型 Skill。它会先把用户的原始请求整理成简报、顶层 goal 草稿、完成标准、验证方式和可并行处理的子目标提示。

## Why It Helps

This Skill is useful when a task is too large, vague, or multi-part to execute safely in one pass.

它适合处理那些范围较大、描述模糊、需要拆分协作的任务。

![Parallel subgoals](assets/images/02-parallel-subgoals.png)

Key advantages:

- **Clear planning boundary**: Skill trigger does not automatically create a Codex goal.
- **Safer execution**: real goal creation happens only after the user explicitly asks for it.
- **Better parallel work**: sub-goals are designed to be independent, bounded, and easier to merge.
- **Built-in validation**: each plan includes success criteria and checks before reporting completion.
- **Less accidental scope creep**: the main agent rejects unrelated refactors and unverified agent claims.

核心优势：

- **规划和执行分离**：触发 Skill 不等于自动创建 Codex goal。
- **执行更安全**：只有用户明确要求时，才进入真实 goal 创建和执行。
- **并行更清晰**：子目标强调独立、边界明确、结果容易综合。
- **自带验证意识**：计划会包含完成标准和验证方式。
- **减少范围漂移**：避免“顺手重构”和未经验证的代理结论。

## How To Use

Install the Skill into your Codex skills directory:

```bash
mkdir -p "$HOME/.codex/skills/codex-goals-for-a-task"
cp skills/codex-goals-for-a-task/SKILL.md "$HOME/.codex/skills/codex-goals-for-a-task/SKILL.md"
```

Then start a new Codex thread and ask for planning:

```text
Use codex-goals-for-a-task to turn this project into an execution brief and parallel sub-goals. Do not create a real goal yet.
```

中文使用方式：

```text
用 codex-goals-for-a-task 帮我把这个项目生成计划简报和并行子目标。先不要创建真实 goal。
```

When the plan looks right, explicitly ask Codex to create and execute the goal:

```text
Create the Codex goal from this brief and execute it.
```

当计划确认无误后，再明确要求：

```text
根据这个简报创建 Codex goal 并执行。
```

![Plan first, execute later](assets/images/03-plan-first-execute-later.png)

## Example Output

The Skill produces a planning package like this:

```text
Brief:
Build a focused implementation plan for the requested project. Include the core deliverables, behavior expectations, quality constraints, and validation steps.

Top-level goal:
Create a complete execution brief and independent sub-goal prompts for the project.

Success criteria:
- The brief has no unresolved placeholders.
- Sub-goals are independent or explicitly marked as sequential.
- Each sub-goal includes context, deliverables, boundaries, and validation.
- The final plan states whether a real Codex goal has been created.

Validation:
- Check that the plan matches the repository context.
- Verify that no execution, file mutation, or agent dispatch happens unless requested.
```

## Safety Boundary

This Skill is intentionally conservative:

- It defaults to planning only.
- It does not create a real Codex goal just because the Skill was triggered.
- It does not dispatch agents unless execution is explicitly requested.
- It treats `/goal ...` inside sub-agent prompts as prompt text, not as proof that a platform-level goal exists.
- It verifies agent claims against source context before using them.

安全边界：

- 默认只生成计划。
- Skill 触发不等于真实创建 Codex goal。
- 不会在用户未确认时派发代理执行。
- 子目标里的 `/goal ...` 只是提示格式，不代表平台已创建 goal。
- 代理结论需要和项目上下文核对后才能采用。

## Repository Contents

```text
skills/codex-goals-for-a-task/SKILL.md
assets/images/
README.md
LICENSE
```

## License

MIT
