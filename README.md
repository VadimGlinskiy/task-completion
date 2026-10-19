# Task Completion

A practical Agent Skill for carrying a scoped software task through implementation, verification, and evidence-based acceptance.

It tells an agent to investigate failures, create focused synthetic tests or fixtures when needed, try reasonable alternate verification routes, and report a real external blocker precisely. It does not permit fabricated evidence, unsafe actions, or bypassing user consent and project rules.

## Install

Install globally for all agents supported by the Skills CLI:

~~~powershell
npx skills add <OWNER>/task-completion --skill task-completion --global --agent '*' --yes
~~~

Or target specific agents without installing any agent applications:

~~~powershell
npx skills add <OWNER>/task-completion --skill task-completion --global --agent codex --agent antigravity --agent hermes-agent --agent github-copilot --yes
~~~

Replace <OWNER> with the GitHub account or organization that hosts this repository. The CLI writes the skill to the selected agents' skill directories. The supported targets include Codex, Antigravity, Hermes Agent, and GitHub Copilot; see the [Skills CLI agent list](https://github.com/vercel-labs/skills#supported-agents).

To install into the current project instead of globally, omit --global.

## Update or remove

~~~powershell
npx skills update task-completion --global
npx skills remove task-completion --global
~~~

## What the skill asks an agent to do

1. Read the project's instructions and define the requested scope.
2. Resolve required direct and transitive dependencies in order, accept each with evidence, then return to the original task.
3. Implement the complete in-scope change, including focused test support when needed.
4. Run relevant acceptance checks and fix failures caused by the change.
5. If a route is unavailable, try safe isolated alternatives and state exactly what the evidence proves.
6. Leave work open only for a genuine external constraint, with the blocked criterion and attempted alternatives recorded.
7. Finish with an accurate summary of changes, checks, and remaining risks.

## Limits

A skill is guidance loaded by an AI agent, not an enforcement mechanism. An agent can still ignore it, and it cannot override the user's request, repository rules, access controls, safety requirements, or missing external access. The skill requires honest reporting; it does not claim that every task can be completed regardless of those constraints.

## Repository layout

~~~text
skills/task-completion/SKILL.md
~~~

## Use in a project

Add a project instruction such as this to its AGENTS.md:

> For implementation tasks, use the task-completion skill when available. Complete focused acceptance for the current task, and report only evidence-backed results.

Keep project-specific acceptance rules in the project instructions; this skill provides the general completion workflow.
