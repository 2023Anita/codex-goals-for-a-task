<p align="center">
  <img src="assets/images/01-from-messy-task-to-goal-brief.png" alt="codex-goals-for-a-task turns a messy task into a goal brief" width="920">
</p>

<h1 align="center">codex-goals-for-a-task</h1>

<p align="center">
  <strong>A planning-first Codex Skill for turning vague requests into execution briefs, goal drafts, and parallel sub-goals.</strong>
</p>

<p align="center">
  <a href="skills/codex-goals-for-a-task/SKILL.md"><img alt="Codex Skill" src="https://img.shields.io/badge/Codex-Skill-111827?style=for-the-badge"></a>
  <img alt="Planning first" src="https://img.shields.io/badge/Mode-Plan%20First-2563eb?style=for-the-badge">
  <img alt="Goal safe" src="https://img.shields.io/badge/Goal-Safe%20Boundary-16a34a?style=for-the-badge">
  <a href="LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/License-MIT-f59e0b?style=for-the-badge"></a>
</p>

<p align="center">
  <a href="#-english">🇬🇧 English</a>
  ·
  <a href="#-中文">🇨🇳 中文</a>
  ·
  <a href="#-日本語">🇯🇵 日本語</a>
  ·
  <a href="#-한국어">🇰🇷 한국어</a>
</p>

---

## At A Glance

`codex-goals-for-a-task` helps Codex pause before doing work. It converts a raw task into a clear plan that can be reviewed, refined, and only then promoted into a real Codex goal.

`codex-goals-for-a-task` 会让 Codex 先停下来做规划：把原始任务整理成可审阅、可改进、可验证的执行方案，然后再由用户决定是否创建真实 Codex goal。

| What goes in | What comes out |
| --- | --- |
| A vague task request | A filled execution brief |
| A large multi-part project | A top-level goal draft |
| A risky “just do it” instruction | Success criteria and validation checks |
| A task that may need parallel agents | Independent bounded sub-goal prompts |

> **Core rule:** Skill trigger does not automatically create a Codex goal.<br>
> **核心规则：** 触发 Skill 不等于自动创建 Codex goal。

## How It Works

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>1. Brief</h3>
      <p>Turn a messy request into a concrete execution brief with scope, deliverables, constraints, and validation.</p>
    </td>
    <td width="33%" valign="top">
      <h3>2. Split</h3>
      <p>Break the work into independent sub-goals only when parallel work is actually useful.</p>
    </td>
    <td width="33%" valign="top">
      <h3>3. Confirm</h3>
      <p>Create and execute a real Codex goal only after the user explicitly asks for it.</p>
    </td>
  </tr>
</table>

<p align="center">
  <img src="assets/images/02-parallel-subgoals.png" alt="Parallel sub-goals are bounded and independent" width="760">
</p>

## Why It Feels Better

| Capability | Why it matters |
| --- | --- |
| Planning-first workflow | Reduces accidental execution and makes the work reviewable. |
| Explicit goal boundary | Keeps Codex goal creation under user control. |
| Parallel-ready prompts | Gives each agent context, deliverables, boundaries, and validation. |
| Conflict-aware synthesis | The main agent checks results against source context before using them. |
| Scope discipline | Avoids unrelated refactors, vague “improvements,” and unverified claims. |

## Install

```bash
mkdir -p "$HOME/.codex/skills/codex-goals-for-a-task"
cp skills/codex-goals-for-a-task/SKILL.md "$HOME/.codex/skills/codex-goals-for-a-task/SKILL.md"
```

Then start a new Codex thread so the Skill list can refresh.

## Quick Start

Generate a plan first:

```text
Use codex-goals-for-a-task to turn this project into an execution brief and parallel sub-goals. Do not create a real goal yet.
```

After reviewing the plan, explicitly execute:

```text
Create the Codex goal from this brief and execute it.
```

<p align="center">
  <img src="assets/images/03-plan-first-execute-later.png" alt="Plan first, execute later after user confirmation" width="760">
</p>

## Example Plan Shape

```text
Brief:
Build a focused implementation plan for the requested project. Include core deliverables, behavior expectations, quality constraints, and validation steps.

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

## 🇬🇧 English

Use this Skill when you want Codex to plan a complex task before acting. It is especially useful for large features, repo changes, research tasks, UI builds, multi-agent workflows, and any request where execution should be separated from approval.

The Skill creates a planning package first. It does not automatically create a Codex goal, dispatch agents, mutate files, or start execution unless the user clearly asks for that next step.

## 🇨🇳 中文

当你希望 Codex 先把复杂任务规划清楚，再决定是否执行时，可以使用这个 Skill。它适合大型功能、仓库改造、研究任务、界面构建、多代理协作，以及任何需要把“计划”和“执行”分开的场景。

这个 Skill 默认只生成计划包。它不会因为被触发就自动创建 Codex goal、派发代理、修改文件或开始执行；只有用户明确要求下一步时才会继续。

## 🇯🇵 日本語

Codex にすぐ作業させる前に、複雑なタスクを整理したいときに使う Skill です。大きな機能開発、リポジトリ変更、調査、UI 制作、マルチエージェント作業などに向いています。

この Skill はまず計画パッケージを作ります。Skill が起動しても、Codex goal の作成、エージェント実行、ファイル変更、実作業は自動では始まりません。ユーザーが明示的に依頼した場合だけ次に進みます。

## 🇰🇷 한국어

Codex가 바로 실행하기 전에 복잡한 작업을 먼저 정리하고 싶을 때 사용하는 Skill입니다. 큰 기능 개발, 저장소 변경, 리서치, UI 작업, 멀티 에이전트 워크플로우처럼 계획과 실행을 분리해야 하는 상황에 적합합니다.

이 Skill은 먼저 계획 패키지를 만듭니다. Skill이 실행되었다고 해서 Codex goal 생성, 에이전트 실행, 파일 수정, 실제 작업이 자동으로 시작되지는 않습니다. 사용자가 명확히 요청한 경우에만 다음 단계로 진행합니다.

## Repository Map

```text
skills/codex-goals-for-a-task/SKILL.md   # The Codex Skill
assets/images/                           # README illustrations
README.md                                # GitHub project page
LICENSE                                  # MIT License
```

## Design Notes

This README uses a GitHub-friendly project-page pattern: strong visual hero, badges, language shortcuts, feature cards, a short mental model, and concrete usage examples. The layout is intentionally static Markdown/HTML so it renders well on GitHub without a build step.

## License

MIT
