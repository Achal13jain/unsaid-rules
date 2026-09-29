# Portability - version 1.0.0

Keep the core skill instructions and references unchanged across hosts. This version requires no API key, network service, runtime dependency, or executable helper. Optional repository access can establish facts, but the skill also works from supplied context.

## Claude Code marketplace plugin

The repository root is both the marketplace root and the plugin root. Its `.claude-plugin/marketplace.json` entry points to `.`, while `.claude-plugin/plugin.json` supplies the matching `unsaid-rules` plugin name. Claude Code discovers the existing `skills/client-judgment/` directory through the plugin's standard `skills/` layout.

Add the marketplace and then install its plugin as separate steps:

```bash
claude plugin marketplace add Achal13jain/unsaid-rules
claude plugin install unsaid-rules@unsaid-rules
```

The first command registers the marketplace; it does not install the plugin. Invoke the installed plugin skill as:

```text
/unsaid-rules:client-judgment
```

In Claude Code's UI, open **Manage Plugins**, select **Marketplaces**, choose **Add**, and enter `https://github.com/Achal13jain/unsaid-rules`. After the marketplace appears, install **Unsaid Rules** from its plugin listing.

## Standalone skill

Install directly with the Skills CLI:

```bash
npx skills add Achal13jain/unsaid-rules --skill client-judgment
```

Or copy the whole `client-judgment` folder, retaining `SKILL.md`, `references`, `assets`, and `agents`. The `agents/openai.yaml` file is optional OpenAI UI metadata. Other hosts can ignore it.

| Host | Project location | Invocation example |
| --- | --- | --- |
| Claude Code | `.claude/skills/client-judgment/` | `/client-judgment` followed by the request |
| Codex CLI/IDE | `.agents/skills/client-judgment/` | `$client-judgment` followed by the request |
| Antigravity | `.agents/skills/client-judgment/` | Ask the agent to use the client-judgment skill |

Do not keep both the Claude Code plugin and a standalone copy in a directory Claude Code scans. Choose one installation method so the same skill is not loaded twice. To switch methods, remove or disable the existing copy before installing the other one.

Use the host's skill discovery UI to confirm installation. Automatic activation varies by host; invoke the skill explicitly when assessing behavior. A portable format cannot ensure identical model outputs.

For a chat interface without skill installation, attach the instructions and relevant references and ask the model to follow them for the task. This is a manual context fallback, not native installation or guaranteed automatic activation.

## Example request

Use client-judgment to draft a short client reply. The client asks whether the website can be shared with prospects. Facts: production mobile/tablet checks passed, inquiry delivery passed, no known blockers remain. Do not add a new deadline or an extra approval step.

## Official references consulted (28 September 2026)

- https://code.claude.com/docs/en/plugin-marketplaces
- https://code.claude.com/docs/en/plugins-reference
- https://code.claude.com/docs/en/plugins/install
- https://code.claude.com/docs/en/skills
- https://developers.openai.com/codex/skills
- https://antigravity.google/docs/skills

Check current host documentation before publishing installation claims, and keep client examples anonymized.
