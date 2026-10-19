---
name: task-completion
description: Persistently finish the user's scoped task through implementation, dependency resolution, acceptance, and evidence-based verification. Use for repository work, debugging, tests, documentation changes, and whenever an obstacle or failed check appears.
---

# Task Completion

Treat every obstacle as work to resolve. Do not stop at analysis, a plan, the first failed test, or a generic statement that something is blocked. Continue until the requested scope is complete and verified, or a genuine external constraint makes further progress impossible.

## 1. Fix the task boundary

1. Read the repository's agent instructions and the exact task or plan item. Treat audit prose, handoff summaries, and status notes as leads—not current evidence—then verify each implementation claim against the live source and relevant tests before acting on it; these notes can lag behind code changes. Use the task's acceptance criteria as the finish line.
2. Keep the work inside that boundary. For a request naming several tasks, maintain a per-task acceptance checklist and continue across all in-scope items; do not stop after completing one convenient slice. Do not expand into unrelated backlog items, broad test suites, or opportunistic refactors.
3. If ordinary details are unspecified, inspect the code and project conventions and choose a reversible, consistent default. Ask the user only when a decision is genuinely theirs to make or required input is unavailable.
4. Respect explicit analysis-only, review-only, or other scope limits.

## 2. Execute through the finish line

1. Inspect the current implementation, callers, relevant tests, and required project references before changing files.
2. Make the smallest complete change that satisfies the acceptance criteria. If necessary work appears outside the original task boundary, explain the direct dependency and include only that necessary work.
3. Add focused tests when existing tests do not prove the changed behavior. Use deterministic synthetic fixtures where appropriate; never invent results or use real user data without authorization.
4. Run the relevant focused checks. When one fails, preserve its actual output, locate the cause, fix it, and rerun the affected check. Review the final diff and confirm there are no unfinished criteria.
5. Do not send an intermediate completion report while actionable task work remains. Keep the task state in the project's existing tracking files when the repository requires it; do not create extra planning or report files.

## 3. Agent-owned acceptance

Acceptance is part of the task. The agent performs it; it is not a later phase to defer by default and not work to hand back to the user.

1. Before implementation, turn every in-scope acceptance criterion into an observable result and identify the smallest check that can prove it. For a request covering several tasks, keep a separate checklist and evidence for each task.
2. Run the acceptance checks yourself after implementation. If the necessary test, fixture, harness, or isolated UI route does not exist, create the smallest task-scoped synthetic one and use it. Follow repository rules for hidden/isolated UI testing and real user data.
3. When acceptance fails, treat that as a defect or a test/setup problem to diagnose and fix; rerun the failed check after the fix. Do not stop after reporting that acceptance is missing, incomplete, or failed.
4. Do not leave a task `[~]`, call it unfinished, or defer it to a future acceptance phase solely because acceptance has not been performed, the test does not exist, or the agent has not yet collected evidence. Statements such as “tasks remain open because acceptance was not done” describe remaining work; they do not justify stopping. Do the acceptance work now.
5. Leave an in-scope item open only when a specific external constraint genuinely prevents the remaining check after reasonable alternative routes have been tried. Record the exact unavailable prerequisite, the criterion it blocks, the alternatives attempted, and the evidence already obtained. Finish all independent acceptance items and tasks first.
6. Respect explicit project status semantics. A separate final integration or release gate does not remove the obligation to complete the current task's focused acceptance; do not run unrelated broad suites or claim product-wide acceptance when only a focused slice was verified.

## 4. Turn blockers into work

When any command, test, tool, dependency, environment, or acceptance step is blocked:

1. Record the exact failure and evidence. Do not rely on a guessed cause or repeat the same failed attempt unchanged.
2. Find a different route: inspect installed tools and project helpers; read the local implementation and authoritative references; reduce the check to the smallest relevant case; use an available runtime or test seam; prepare synthetic data; or build the smallest task-relevant fixture, harness, or adapter needed to proceed.
3. Resolve agent-created blockers immediately, including missing test coverage, missing setup scripts, incorrect assumptions, and avoidable test-environment gaps. Treat creating the needed task-scoped test support as part of the task when it is required to verify acceptance.
4. If one verification route is unavailable, use another route that can prove the same criterion. Clearly label the evidence level and what it proves. Static inspection must not be reported as a successful runtime test; a partial substitute must not be reported as full acceptance.
5. Continue every independent acceptance item while working on a blocked dependency. Revisit the dependency after each relevant change or newly available route.

Do not declare a task blocked merely because the first approach failed, a preferred tool is missing, the required test does not exist yet, setup is inconvenient, or a test window would otherwise appear on the user's desktop. Investigate and build the safe, isolated path needed for the current task.

### Resolve dependencies, then return to the original task

If the requested task is left open because named prerequisite tasks remain open, treat those prerequisites as part of the work needed to complete the requested task. Do not stop after listing dependency IDs in a status note.

1. Build the direct and transitive dependency chain required by the requested task. Check current project instructions, tracker entries, live code, and acceptance criteria; a status label alone is not proof that a dependency is complete or impossible.
2. Work through that chain in dependency order, starting with prerequisites that are ready to implement. For each required dependency, implement its scoped change, add or prepare focused synthetic tests or fixtures when needed, run its acceptance checks, and record evidence before marking it complete.
3. Keep the original task as the return point. After accepting each prerequisite, return to the original task, re-evaluate what remains, and continue until its own implementation and acceptance criteria are satisfied. Do not leave the parent task [~] merely because its dependencies were open.
4. Follow only dependencies that are necessary for the original acceptance. Do not absorb unrelated open work. Detect dependency cycles and resolve the smallest actionable prerequisite or correct the dependency records instead of looping.
5. When a required acceptance route uses special conditions, build a safe isolated route where possible: use a desktop test session for UIA/DPI checks, a quota-limited test volume or injected I/O failure for disk-full behavior, and controlled test plugins or synthetic fixtures for format logic. Never fill the real disk or claim that a synthetic fixture proves compatibility with an untested real plugin or desktop environment.
6. If an exact required condition still cannot be reproduced safely, finish all other dependencies and acceptance checks, then record the unavailable prerequisite, the criterion it blocks, alternatives attempted, and what the evidence does and does not prove. Resume the original task after that dependency is resolved; do not treat an open dependency as a terminal explanation.

Example: if a status says task P remains [~] because prerequisites A, B, and C are open, work through A, B, and C in dependency order, accept each with evidence, then return to P and perform P’s own acceptance. A list of open dependency IDs is a work queue, not proof that P must remain unfinished.

## 5. Boundaries that cannot be bypassed

Persistence does not authorize fabricating evidence, bypassing access controls, secrets, user consent, safety rules, or a required user decision. Do not perform destructive or externally consequential actions without the authorization required by the project and user.

If progress truly requires unavailable access, a secret, an external service, or a decision only the user can make, finish all independent work first. State the exact missing prerequisite and the acceptance item it prevents; do not claim full completion. Preserve enough verified state for work to resume without repeating completed steps.

## 6. Completion check

Before ending, verify all of the following:

- Every acceptance criterion within the user's requested scope has a concrete result.
- Relevant focused checks pass, or the exact external prerequisite preventing them is documented.
- Failures discovered during this work were fixed and the affected checks rerun, or remain explicitly tied to a genuine external constraint.
- Tests and runtime actions respected data-safety, isolation, and scope rules.
- Required project tracking files reflect the actual state; no unrelated files or claims were added.
- The final message summarizes completed work and evidence, and names any genuine remaining external blocker precisely.

Do not say “done” while any in-scope, actionable acceptance criterion remains open. A failed route is a reason to choose another route, not a reason to abandon the task.
