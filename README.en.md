# KOL Order Feishu Writeback / KOL 订单飞书回写

[简体中文](README.md) | **English**

Write verified Shopify order numbers and KOL codes/Impact IDs to the specified Feishu records and read them back.

[Download complete project ZIP](https://github.com/hezonglinhzl-creator/varla-electric-mobility-skills-and-tools/raw/main/packages/skill-varla-kol-feishu-order-writeback-skill.zip) · [All projects](https://github.com/hezonglinhzl-creator/varla-electric-mobility-skills-and-tools)

## Features

- Email-first exact matching
- Narrow order-field updates
- Readback verification

## What is included

| Part | Location |
| --- | --- |
| Local Feishu OpenAPI Toolkit | [feishu-codex-local](apps/feishu-codex-local/README.en.md) |
| Shopify KOL Browser Order Tool | [shopify-order-bot](apps/shopify-order-bot/README.en.md) |
| Skill instructions | [SKILL.md](skill/varla-kol-feishu-order-writeback-skill/SKILL.md) |

## Download and extract

1. Open this repository, choose **Code → Download ZIP**, or use the complete-project download above.
2. Right-click the downloaded ZIP and choose **Extract All**. Open the extracted folder containing this README.
3. Keep the whole folder together. Start the program first using the next section, then install/use its skill.

Installation also writes PACKAGE-LOCATION.json beside the installed SKILL.md, mapping the bundled programs to their actual extracted directories. Keep the full extracted folder; rerun the installer after moving it. Existing Skill content is preserved by default while paths are refreshed.

## 1. Set up the program first

### Local Feishu OpenAPI Toolkit (`feishu-codex-local`)

Windows, Python and your Feishu app permissions; chat bridging is optional.

Open `apps/feishu-codex-local` first. Documents, native tables, Base records and attachments, with setup/check scripts.

1. Run `配置OpenAPI.bat` and enter your own App ID and App Secret.
2. Configuration stays locally at `%USERPROFILE%\.feishu-docs\config.json`.
3. Run `检查OpenAPI.bat`; add required permissions and publish your app version in Feishu if needed.
4. Run `python scripts/feishu_docs.py --help`, or ask Codex with the installed skill to read a specified document first.
5. Only chat-to-Codex bridging needs the separate bridge installation/configuration and cc-connect. OpenAPI data operations can run independently.

[Full program / browser-extension guide](apps/feishu-codex-local/README.en.md)

Unauthorized resources remain inaccessible. Do not upload your config or treat a failed check as a successful sync.

### Shopify KOL Browser Order Tool (`shopify-order-bot`)

Python 3.11+, AdsPower Local API and your Shopify admin access.

Open `apps/shopify-order-bot` first. Single-order Excel validation, address checks, fill and a separate submit step.

1. Run `python -m pip install -r requirements.txt`, then `python -m playwright install chromium`.
2. Copy `.env.example` to `.env` and enter your AdsPower API settings, profile ID and SHOPIFY_ADMIN_URL.
3. Prepare `KOL_order.xlsx` using this folder's documented headers; start with one synthetic test row.
4. Run `python main.py --step adspower`, then `python main.py --step browser` and log in to your own profile.
5. Run `python main.py --step fill` and review before submission. Execute real submission only when explicitly authorized.

[Full program / browser-extension guide](apps/shopify-order-bot/README.en.md)

Private configuration, login sessions and order workbooks must be supplied by the operator.

## 2. Install the Skill

1. At the extracted project's root, double-click `安装Skill.cmd` on Windows.
2. The installer copies `skill/varla-kol-feishu-order-writeback-skill` to `%USERPROFILE%\.codex\skills\varla-kol-feishu-order-writeback-skill`. Existing same-name skills are skipped; check the displayed result.
3. Reopen Codex and start a new chat. Use the exact skill name shown below.
4. If scripts cannot run under your organization policy, open install.ps1 for review or copy the skill directory manually to the same destination.

## 3. First task

| Prepare | Details |
| --- | --- |
| Input | Current Feishu Base link, confirmed order results and update scope. |
| Output | Creator/order mappings, update receipts and readback results. |

```text
Use varla-kol-feishu-order-writeback-skill to read my Base, match this confirmed order by email and show proposed field changes before writing.
```


## Limits and troubleshooting

Do not guess records from row position or names. Order creation and shipment are separate facts; update status only when confirmed.

| Problem | Next step |
| --- | --- |
| Skill not visible | Check the installer output and destination SKILL.md, reopen Codex and start a new chat. |
| Program fails to start | Open its directory in PowerShell and run the documented command so the error remains visible; check that program's README. |
| Browser panel missing | Select the exact folder containing manifest.json, check supported websites and refresh the website tab. |
| External service unavailable | Supply your own authorization/settings and verify access. Keep local output rather than claiming a sync/send succeeded. |

## Privacy and status

This is a source/skill distribution. No real accounts, OAuth tokens, customer/KOL lists, contracts, orders, mailbox exports or business media are included. You configure your own services. Documentation and package paths were checked; live orders, sends and publications were not executed as part of documentation validation.
