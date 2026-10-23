# Publisher application record

Submitted on 2026-10-23 JST after the owner explicitly approved the Publisher Terms. The confirmation page displayed “Thanks for applying” and confirmed receipt. Approval and Marketplace listing are pending. This document records the public field values; private contact details are omitted.

## Public information

| Item | Submitted value |
| --- | --- |
| Organization name | SIMD LLC |
| Organization handle | `kamuidash` (submitted; final namespace approval pending) |
| Plugin name | KamuiDash |
| Plugin identifier | `kamuidash` |
| Version | `1.0.0` |
| Repository | https://github.com/kamui-project/kamuidash-cursor |
| Website | https://dashboard.kamui-platform.com/ |
| Logotype URL | https://raw.githubusercontent.com/kamui-project/kamuidash-cursor/main/assets/marketplace-logo.svg |
| Category, if requested | Developer Tools / Cloud Infrastructure, using the closest available option |
| Support | https://dashboard.kamui-platform.com/en/inquiry |
| Privacy policy | https://dashboard.kamui-platform.com/en/documents/privacy-policy |
| Terms | https://dashboard.kamui-platform.com/en/documents/terms-of-use |
| Pricing | https://dashboard.kamui-platform.com/en/documents/spec-price-overview |

The contact email was explicitly supplied by the owner and entered in the private application; it is not copied into this public document. Owner is a disabled field and the form displays “Submitting as an individual.” The organization display fields do not change the underlying account owner. The form states that clicking Submit Application acknowledges agreement to the Publisher Terms; the owner explicitly approved those terms before the application was submitted.

## Short description

Inspect apps, deployment status, and logs, and deploy GitHub-backed apps on KamuiDash.

## Submitted form description

The form description starts with a company-submission note naming **SIMD LLC** and the owner-approved review contact email. The contact address is omitted from this public copy.

KamuiDash connects Cursor to the apps you own on KamuiDash through a remote MCP server. Inspect projects, apps, deployment status, and logs; discover connected GitHub repositories and branches; and, with explicit confirmation, deploy or update apps, create databases, or configure custom domains.

The plugin uses browser-based OAuth with the existing KamuiDash service. Repository deployments require the KamuiDash GitHub App to have access to the selected repository. Application secrets and billing settings are managed in the KamuiDash dashboard. Resource creation and capacity changes can incur charges under KamuiDash pricing. Deployment requests are asynchronous and must be checked before reporting an app as live.

The public repository includes the Cursor plugin manifest, remote MCP configuration, logo, MIT license, and English/Japanese setup documentation. The MCP health and OAuth discovery endpoints have been checked; Cursor-specific end-to-end authentication and tool execution are pending verification.

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

The inspected form requests Organization name, Organization handle, Contact email, Logotype URL, Description, GitHub repository, and Website URL, and displays a fixed Owner. It does not currently show a demo-video or reviewer-credentials field. Review all values and the [Publisher Terms](https://cursor.com/marketplace-publisher-terms) before submission. Cursor-specific end-to-end checks remain pending. Submission was completed after explicit owner approval; the confirmation page established receipt, not approval.

## Company submission and fixed Owner field

The owner requested submission for **SIMD LLC**. Organization name and the plugin manifest author use the English display name SIMD LLC. The description explicitly states that the company is submitting KamuiDash. The fixed Owner field still shows the signed-in individual account; entering a company name does not change account ownership.

Cursor staff recommended identifying the company and preferred contact in the description when the form cannot switch Owner to a company. See the [official forum response](https://forum.cursor.com/t/cursor-plugin-submit-as-company-not-individual/156274). The application has been submitted and receipt confirmed; the fixed individual Owner was not changed by the company display name.
