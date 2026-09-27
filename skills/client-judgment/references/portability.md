# Portability — version 1.0.0

Keep the core skill instructions and references unchanged across hosts. This version requires no API key, network service, package installation, or executable helper. Optional repository access can establish facts, but the skill also works from supplied context.

## Install from a downloaded source folder

Copy the whole `client-judgment` folder, retaining `SKILL.md`, `references`, `assets`, and `agents`. The `agents/openai.yaml` file is optional OpenAI UI metadata. Other hosts can ignore it.

| Host | Project location | Invocation example |
| --- | --- | --- |
| Claude Code | `.claude/skills/client-judgment/` | `/client-judgment` followed by the request |
| Codex CLI/IDE | `.agents/skills/client-judgment/` | `$client-judgment` followed by the request |
| Antigravity | `.agents/skills/client-judgment/` | Ask the agent to use the client-judgment skill |

Use the host's skill discovery UI to confirm installation. These are documentation-based instructions, not a claim that this package has been installed and tested in all three products. Automatic activation varies by host. Explicitly invoke it when assessing behavior. A portable format cannot ensure identical model outputs.

For a chat interface without skill installation, attach the instructions and relevant references and ask the model to follow them for the task. This is a manual context fallback, not native installation or guaranteed automatic activation.

## Example request

Use client-judgment to draft a short client reply. The client asks whether the website can be shared with prospects. Facts: production mobile/tablet checks passed, inquiry delivery passed, no known blockers remain. Do not add a new deadline or an extra approval step.

## Official references consulted (27 September 2026)

- https://code.claude.com/docs/en/skills
- https://developers.openai.com/codex/skills
- https://antigravity.google/docs/skills

Check current host documentation before publishing installation claims, and keep client examples anonymized.
