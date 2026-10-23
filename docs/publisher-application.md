# Publisher application draft

Prepared on 2026-10-23 JST. The application requires Cursor sign-in. The signed-in form's current fields have not yet been inspected, so these are reusable draft values, not a claim that the form has been completed or saved.

## Public information

| Item | Draft value |
| --- | --- |
| Publisher / brand | Kamui |
| Plugin name | KamuiDash |
| Plugin identifier | `kamuidash` |
| Version | `1.0.0` |
| Repository | https://github.com/kamui-project/kamuidash-cursor |
| Website | https://dashboard.kamui-platform.com/ |
| Logo | `assets/logo.png` (512 × 512 PNG) |
| Category, if requested | Developer Tools / Cloud Infrastructure, using the closest available option |
| Support | https://dashboard.kamui-platform.com/en/inquiry |
| Privacy policy | https://dashboard.kamui-platform.com/en/documents/privacy-policy |
| Terms | https://dashboard.kamui-platform.com/en/documents/terms-of-use |
| Pricing | https://dashboard.kamui-platform.com/en/documents/spec-price-overview |

Use the publisher account and contact details approved by the owner. Do not infer a submission identity from a local Git author or GitHub login.

## Short description

Inspect apps, deployment status, and logs, and deploy GitHub-backed apps on KamuiDash.

## Description

KamuiDash connects Cursor to the user's KamuiDash account through a remote MCP server. Developers can inspect projects and apps, investigate deployment history and runtime logs, discover connected GitHub repositories and branches, and request app creation or updates from a remote GitHub branch. The service also exposes tools for static sites, databases, and custom domains.

The plugin uses browser-based OAuth with the existing KamuiDash service. Access follows the connected account's permissions; the service is not limited to read-only access or a single project. Repository deployment requires the KamuiDash GitHub App to have access to the selected repository. Application secrets and billing settings are managed in the KamuiDash dashboard.

App and database provisioning or capacity changes can incur charges under KamuiDash pricing. Deployment requests are asynchronous, and users must inspect deployment and runtime status before treating an app as live. The repository includes setup instructions, usage examples, and links to pricing, privacy, terms, and support.

## Suggested use cases

1. Inspect projects and apps without leaving the coding environment.
2. Diagnose deployment failures using deployment and runtime logs.
3. Deploy or update an app from a connected GitHub branch after confirming the target and resource settings.

## Current verification statement

The plugin manifest, MCP connection configuration, logo reference, and relative documentation links have been checked. The public MCP health and OAuth discovery endpoints responded successfully. Unauthenticated initialization and tool discovery requests made with curl returned HTTP 401 with an OAuth resource-metadata challenge.

Cursor plugin loading, browser consent, token exchange, authenticated tool discovery, and resource operations have not yet been verified in Cursor. Do not submit a claim that those checks passed until they have actually been performed. See the [reviewer walkthrough](reviewer-walkthrough.md) for the planned checks.

## Review access and demo

If the form requests test access or a demo video, provide them through the private application channel after the owner approves the dedicated test account and any resource charges. Do not add passwords, tokens, private repository links, or account/project identifiers to this public repository.

No Cursor demo video has been recorded for this package. Prior tests in other MCP clients do not establish Cursor compatibility.

## Final submission

Confirm the form's exact requested fields after signing in at https://cursor.com/marketplace/publish. Review the [Publisher Terms](https://cursor.com/marketplace-publisher-terms) before agreeing. This draft does not accept terms or submit an application.
