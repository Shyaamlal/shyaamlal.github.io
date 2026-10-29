# Test design and evidence

Use with the [delivery workflow](01-delivery-workflow.md). The task supplies the business requirements; these principles guide implementation and review.

## Check the business result

- State the scenario summary, meaningful test steps and expected result for each step. Keep business assertions visible and explain how they check those expectations.
- Check persisted state after a save. A click or successful response alone does not establish that the intended result was stored.
- Before asserting absence, establish that the relevant operation and UI loading have completed. A temporary count of zero is not enough.
- Prefer observed, user-facing locators scoped to the correct region, row or dialog. Use condition-based waits for meaningful state changes rather than delays or retries that hide failures.
- Reuse confirmed helpers and UI-map knowledge. Update the UI map when new interactions have been verified.

## Own the data and cleanup

- Validate required input data before acting. Keep identifiers intact, including leading zeros where applicable.
- Change only the approved, uniquely identified data. Do not delete unrelated or ambiguous records.
- Attempt required cleanup even when the test or another cleanup action fails. Preserve the original failure and expose cleanup failures.
- If required cleanup fails, the test fails even when its business assertions passed.

## Make evidence reviewable

- Present a table of scenario summary, steps and expected results. Connect each expectation to its assertion and run evidence; descriptions alone are not verification.
- Generate actual results from execution and assertion outcomes. For full review runs, retain step screenshots, execution reports and relevant traces through the project's reporting implementation.
- Put data prerequisites and test boundaries into the task explicitly. Record missing evidence and incomplete checks instead of treating them as a pass.
- Include code-version information where supported. A commit hash with an uncommitted-changes marker does not identify the exact contents of those changes.

## Check the test itself

- Run the project's configured offline verification before review. The example uses `npm run verify` for type-checking and selected test, runner, catalog and relative-link checks. Verify the command's actual scope in your project.
- For tasks that both change shared data and lack required live test data, use selected synthetic checks where appropriate: run the actual script against controlled page states that represent relevant failure conditions.
- State the expected response to each condition: fail an assertion, refuse an unsafe action, preserve unrelated data or report cleanup failure. An arbitrary error is not sufficient evidence.
- Verify the synthetic harness is isolated from the shared application. Retain results and failure traces. Read-only tests skip this additional harness, not the relevant baseline checks.
- Synthetic checks cover the simulated conditions. They do not complete live business acceptance.

## Live acceptance

The implementation agent runs the approved staging tests. Live business acceptance requires five passing staging runs with retries disabled, followed by human evidence review and confirmation. If required staging data is unavailable, code may be merged after the agreed checks and approvals. Keep business acceptance pending until the required staging evidence and human review are complete.
