# Task Completion

A general-purpose Agent Skill for finishing scoped work with evidence-based acceptance.

It applies to code, documentation, debugging, research, and other deliverables. It follows the user's scope and the project's own rules; it does not assume a language, framework, test runner, repository layout, or agent-specific tool.

## Install

Install globally for all agents detected by the Skills CLI:

~~~powershell
npx skills add VadimGlinskiy/task-completion --skill task-completion --global --agent '*' --yes
~~~

To install only in the current project, remove the --global option.

The skill is located at skills/task-completion/SKILL.md. The Skills CLI supports multiple agents and project-level or global installation; see the [CLI reference](https://github.com/vercel-labs/skills/blob/main/docs/commands.md).

## What it does

- Defines the requested outcome, constraints, and observable completion criteria.
- Inspects the current implementation and relevant evidence before changing anything.
- Resolves only dependencies required by the requested outcome, then returns to the original task.
- Completes the work and performs focused, risk-appropriate verification.
- Distinguishes a fixed defect, a disproved hypothesis, and a genuine external blocker.
- Reports what changed, what was checked, and what remains uncertain.

## Use in a project

Add a short instruction to the project's agent guidance file (for example, AGENTS.md, CONTRIBUTING.md, or the equivalent):

> For implementation tasks, use the Task Completion skill when available. Complete the requested scope, run focused acceptance checks appropriate to the change, and report evidence and remaining limitations.

Keep project-specific policies and acceptance criteria in the project guidance. This skill provides a reusable completion workflow.

## Examples

- **Code change:** fix the behavior, run the smallest relevant tests, and report the command and result.
- **Documentation change:** edit the requested docs, check links and formatting where practical, and do not run unrelated test suites.
- **External blocker:** finish independent work, try reasonable alternatives, then name the unavailable prerequisite and the exact acceptance item it prevents.

## Limits

A skill is guidance, not an enforcement mechanism. It cannot override the user's request, project instructions, safety requirements, access controls, or missing authorization. It requires honest reporting and does not promise that every task can be completed regardless of external constraints.
