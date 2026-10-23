# Cursor verification and reviewer walkthrough

This is a test plan. None of the Cursor steps below has been recorded as passed.

## Setup

1. Record the Cursor version and test date.
2. Load this repository as a local plugin using the [README instructions](../README.md#install-for-local-evaluation).
3. Confirm that Customize shows `kamuidash` and its MCP server. Use either the plugin or a direct MCP configuration, not both.
4. Authenticate with a dedicated KamuiDash test account. Check the account and scope on the consent screen.
5. For repository tests, arrange a harmless Node.js HTTP demo repository connected through the KamuiDash GitHub App. The app must listen on the platform-provided `PORT` and expose a health endpoint.

Account details, repository identifiers, and target project/app IDs should be shared privately with the reviewer. Do not put credentials into chat or this repository.

## Cases

| Case | Example prompt | Expected result |
| --- | --- | --- |
| Authentication and projects | “List my KamuiDash projects. Do not create or change anything.” | Browser OAuth succeeds, tools are discovered, and project results match the test account's access. |
| App status and logs | “Inspect the latest deployment and runtime logs for the designated test app.” | The agent resolves the intended app and reports actual deployment/runtime state from tool results. Logs do not disclose secrets. |
| GitHub source discovery | “Show the repositories I can deploy and the branches of the designated demo repository.” | The connected demo repository and selected branch can be discovered. Repository contents are unchanged. |
| Create an app | “Help me deploy the demo repository in the designated test project. First show the source branch, runtime, start command, resource size, replicas, public exposure, and applicable pricing.” | After the owner explicitly approves the target and charges, an app can be created. The agent checks deployment and runtime state and verifies the public health endpoint before reporting success. |
| Update the same app | “Use the approved branch to update the same demo app. Show the intended changes and impact first.” | After approval, the agent updates the intended app, tracks the resulting deployment, and verifies its runtime and health endpoint. |
| Invalid target | “Inspect the app with ID not-a-valid-app-id; do not change anything.” | An error or validation response is reported accurately. No app or project is created as a workaround. |

For resource-changing cases, decide the test project, branch, capacity, budget, and cleanup responsibility with the owner first. A plan or demo account is not approval to create billable resources.

## Record results

Keep account-specific evidence private. Record the client version, date, case, pass/fail, and a concise redacted observation. Do not mark a case as passed based on an earlier run in Claude or another MCP client.

The cases above cover representative flows, not all service tools. Database creation, static-site operations, and custom-domain setup require separate cases if a submission asks for all-tool coverage.

## Before submitting

- Resolve failures or accurately state limitations.
- Update the verification statement in the application draft with the checks actually completed.
- Confirm who owns any test resources and who is responsible for cleanup.
- If requested, record a demo that shows the current Cursor plugin and the flows actually tested, without exposing credentials.
