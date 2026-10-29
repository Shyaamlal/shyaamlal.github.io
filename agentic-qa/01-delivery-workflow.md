# Delivery workflow

You can use these steps as instructions in your own AI harness.

Use alongside [test design and evidence](02-test-design-and-evidence.md) and [agent roles and context](03-agent-roles-and-context.md). These describe the example workflow; adapt its commands, records and approval boundaries before use.

## 1. Select and define the task

- The coordinator checks live issues, pull requests and existing implementation sessions before proposing work.
- The human chooses the task and model. Start one implementation session with a clear scope, its own working copy and branch, and links to the current task records.
- The implementation agent checks relevant existing tests, helpers and UI knowledge before exploring the application again.
- Agree starting data, expected business behaviour, allowed changes, cleanup, evidence and stop conditions. Record observed facts, human decisions, assumptions and unresolved questions distinctly.
- Obtain approval before live exploration/authentication, creating a new task issue and editing the agreed files.

## 2. Implement in the same session

- Explore, clarify, design, implement and make task-related corrections in the same implementation session. Ask routine business questions directly of the human.
- Work in explainable checkpoints. If new evidence changes the task, return to the relevant earlier step and obtain any changed approval.
- Send unrelated defects or new scenarios back to the coordinator for separate tasks; do not silently expand scope.
- The human may shorten the teaching walkthrough for familiar patterns or small maintenance tasks. Required checks, review and approval boundaries remain.

## 3. Run and review

- Run the configured offline verification and record what actually ran. Review the test's business summary, steps and expected results against assertions and execution evidence.
- Obtain approval before staging execution or persistent shared-data changes. Establish owned data and cleanup first; stop when ownership or the starting state is unclear.
- The implementation agent runs the approved staging tests when the required data is available. For live business acceptance in this example, require five passing staging runs with retries disabled, followed by human evidence review and confirmation. This is the business acceptance criterion, not an unconditional prerequisite to merge.
- Update the relevant UI map, test catalog and reusable lessons with the code change. Prepare the Learning Handoff.

## 4. Deliver and reconcile

- Obtain separate human approvals to create the pull request and to merge it. Approval for one does not authorise the other.
- The coordinator checks the actual pull-request state, evidence and human decisions before recording completion.
- If required staging data is unavailable, code may be merged after the agreed checks and approvals while business acceptance remains pending. Record the missing data or run and the remaining five-run acceptance obligation in the task record. Do not equate merge with business acceptance.

## Learning Handoff

Record the task and code changes; approved scope; commands, environment and test selection; run results and cleanup; evidence locations; decisions and reusable lessons; and any unresolved acceptance or follow-up work. Link it from the task issue and pull request so a later session can recover the work.

Never infer an approval from tool access, an issue's existence or silence. These are written workflow rules, not installed technical permission controls.
