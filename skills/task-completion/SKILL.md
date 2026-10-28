---
name: task-completion
description: Finish scoped work with evidence-based acceptance.
version: 1.0.0
author: Vadim Glinskiy (Lord_Inqusitor)
platforms: [windows, macos, linux]
metadata:
  hermes:
    tags: [task-completion, implementation, verification, blockers]
---
# Task Completion

Use this skill to carry a scoped request through implementation and appropriate verification. It applies to code, documentation, debugging, research, and other deliverables. It does not assume a particular language, framework, repository layout, test runner, or agent-specific tool.

## When to Use

- The user asks you to complete, implement, fix, or deliver a bounded outcome.
- A task has required prerequisites, acceptance criteria, or a verification step.
- A failure or unavailable route needs diagnosis before the task can be reported accurately.

Respect analysis-only, review-only, and other explicit scope limits. Do not use persistence as a reason to expand the task.

## Procedure

1. **Define the outcome.** Read the user's request and the relevant project instructions. Identify what should be delivered, the acceptance criteria, constraints, permissions, and any explicit stop conditions. For shared work, inspect the current status and changes before editing.

2. **Inspect current evidence.** Read the implementation, callers, relevant tests, and references needed for this task. Treat old reports and status notes as leads; confirm important claims against the current source or actual outputs. Choose the smallest checks that can prove the requested result.

3. **Resolve required dependencies.** Follow only prerequisites necessary for the requested outcome. Work in dependency order, record evidence for each, then return to the original task. Do not absorb unrelated backlog items. If a dependency is blocked, continue independent work and revisit it when conditions change.

4. **Make the smallest complete change.** Implement the requested behavior without opportunistic refactoring. Add a focused test or fixture when it is needed to prove changed behavior and is allowed by the task. Preserve existing project conventions and user data.

5. **Verify proportionally.** Run the focused checks required by the user or project and those warranted by the change. Do not run unrelated suites. When a check fails, inspect the failure, fix causes within scope, and rerun the affected check. If a verification route is unavailable, try a reasonable alternative and state what that alternative proves and what it does not.

6. **Handle blockers precisely.** Do not call work blocked after the first failed command. Diagnose the failure and try a safe, relevant alternative. A genuine blocker is an unavailable external prerequisite, permission, resource, or user decision that prevents a specific acceptance criterion. Finish independent work, record the alternatives tried, and name the blocked criterion.

7. **Close the loop.** Confirm that every in-scope deliverable has an outcome. Update the project's canonical tracker or handoff only when its rules require it. Report the changes, checks and results, and any remaining limitation. Never claim a check passed unless it actually ran and produced evidence.

## Dependency Work

When a requested outcome depends on other tasks:

1. Map the direct and transitive dependencies that are necessary for acceptance.
2. Complete those dependencies in order, using their own scoped acceptance criteria.
3. Return to the original task after each dependency and reassess what remains.
4. Avoid dependency cycles and unrelated prerequisites.
5. If one exact acceptance condition remains unavailable, finish all independent work and state the missing condition and its impact.

A list of open prerequisites is a work queue, not proof that the requested outcome is impossible.

## Boundaries

- Stop or rescope when the user changes or cancels the request.
- Do not fabricate results, bypass access controls, or exceed user consent.
- Follow the project's data-safety and verification policies.
- Do not turn every task into a test-writing task. Match verification to behavior, risk, and the user's instructions.
- Do not claim product-wide acceptance from a focused check.

## Evidence Examples

- **Code:** name the focused test or build command and its actual result.
- **Documentation:** identify the edited files and relevant formatting, link, or rendering checks.
- **Unverified behavior:** state the static evidence or substitute check and its limits; do not describe it as runtime acceptance.
- **External blocker:** state the unavailable prerequisite, the acceptance criterion it prevents, alternatives attempted, and completed independent work.

## Pitfalls

- Stopping after a plan when implementation was requested.
- Expanding scope to unrelated work because it appears useful.
- Trusting stale summaries instead of checking current source.
- Treating the first failed route as proof that the task is blocked.
- Confusing partial evidence with full acceptance.
- Leaving the user to perform checks that the agent can safely perform itself.

## Completion Check

Before reporting completion, confirm:

- The requested in-scope outcome is delivered.
- Required focused checks ran, or a concrete external blocker is recorded.
- Failures and remaining limitations are described accurately.
- Required project tracking is current, with no unrelated changes included.
