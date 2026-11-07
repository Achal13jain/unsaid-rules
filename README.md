<p align="center">
  <img src="skills/client-judgment/assets/icon.svg" width="96" height="96" alt="Unsaid Rules icon">
</p>

<h1 align="center">Unsaid Rules</h1>

<p align="center">
  <strong>What to say at work, and how to say it.</strong>
</p>

<p align="center">
  <img alt="Version 1.1.0" src="https://img.shields.io/badge/version-1.1.0-2EC9B0">
  <a href="LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/license-MIT-6C63FF"></a>
</p>

Unsaid Rules is a repository of two agent skills for workplace communication:

- **Client Judgment** drafts and reviews client-facing software delivery messages. It keeps the message grounded without hiding limitations or promising work that was never agreed.
- **Corporate Communication** turns rough, casual or emotional writing into clear professional language for the right audience and tone, without changing what you mean.

Client Judgment decides what you can truthfully say and promise. Corporate Communication decides how to say it. For a client delivery message, use both.

## What they help with

Client Judgment:

- Readiness and sign-off questions
- Delays, dependencies, and incidents
- Scope changes and handovers
- Clear ownership without invented deadlines
- Honest pushback when the requested answer is not supported by the facts

Corporate Communication:

- Emails, Slack and Teams messages, status updates and meeting notes, for a manager, colleague, direct report, client, executive, recruiter, external partner or the whole team
- Requests, follow-ups, decisions, apologies, thanks and introductions
- Disagreeing, saying no, pushing back on deadlines, raising concerns, escalating and setting boundaries without losing the point
- Delays, blockers, mistakes and uncertainty, said honestly
- Asking for a raise, resources or new responsibilities, and negotiating scope or priorities
- Turning rough notes or an emotional reaction into a clear message, reviewing a draft, or preparing talking points for a conversation

It chooses a strategy for what the message has to do, then a tone: neutral professional, diplomatic, assertive, warm and collaborative, executive and concise, client-friendly, formal, persuasive, empathetic, or firm but respectful. It writes in plain, natural language, keeps short messages short, and never adds facts, commitments, apologies, blame, concessions or authority that the writer did not give. When a message is about software delivery to a client, Client Judgment decides what can truthfully be said, and factual integrity outranks polish.

## Install

Choose either the Claude Code plugin or the standalone skills. Installing both copies in Claude Code can make the same skill appear twice.

### Claude Code plugin marketplace

In Claude Code, open **Manage Plugins**, select **Marketplaces**, choose **Add**, and enter:

```text
https://github.com/Achal13jain/unsaid-rules
```

Adding the marketplace only makes its catalog available. After it is added, find **Unsaid Rules** in the plugin list and install it. The plugin includes both skills.

The same two steps from a terminal are:

```bash
claude plugin marketplace add Achal13jain/unsaid-rules
claude plugin install unsaid-rules@unsaid-rules
```

Invoke the marketplace-installed skills as:

```text
/unsaid-rules:client-judgment
/unsaid-rules:corporate-communication
```

### Direct skill installation

With the Skills CLI, install each skill you want:

```bash
npx skills add Achal13jain/unsaid-rules --skill client-judgment
npx skills add Achal13jain/unsaid-rules --skill corporate-communication
```

Add `-g` for a global installation. The installer can configure Claude Code, Codex, and other tools that support the Agent Skills format.

Or copy a folder from `skills/` into your tool's skill directory:

| Tool | Project destination | Invoke explicitly |
| --- | --- | --- |
| Claude Code | `.claude/skills/<skill-name>/` | `/client-judgment` or `/corporate-communication` |
| Codex | `.agents/skills/<skill-name>/` | `$client-judgment` or `$corporate-communication` |
| Gemini CLI | `.gemini/skills/<skill-name>/` or `.agents/skills/<skill-name>/` | Ask the agent to use the skill |
| Copilot CLI | `.github/skills/<skill-name>/` | `/client-judgment` or `/corporate-communication` |

Gemini CLI can also install straight from the repository, for example `gemini skills install https://github.com/Achal13jain/unsaid-rules.git --path skills/corporate-communication`. See the [portability guide](skills/client-judgment/references/portability.md) for more invocation examples.

For Claude Code, use either the plugin skills or the standalone skills. If one copy is already installed, remove or disable it before switching installation methods.

## Use them

```text
Use client-judgment. The client asks whether the site is ready for prospect interviews. The inquiry form is disconnected, legal pages still contain placeholders, and mobile checks passed on only two phones. Draft a short, honest reply. No repair date has been agreed.
```

```text
Use corporate-communication. Make this professional for my manager: I did the work, but nobody told me what to do next. Now they're blaming me for the delay.
```

Client Judgment works from three distinctions:

- **Facts:** what was implemented, tested, deployed, or accepted
- **Commitments:** what the sender has agreed or is authorized to promise
- **Next steps:** what can reasonably be proposed without presenting it as completed or scheduled

Corporate Communication works in three steps:

- **Read:** who the message is for, the channel, what you need from them, and what you actually mean
- **Keep:** every fact, request, concern and boundary you wrote, without adding progress, dates, commitments, concessions, blame or authority
- **Write:** plain, specific and calm, led by the point, at the length the channel needs

Ways to use it: ask for a rewrite, name the tone you want, ask to compare two tones, paste rough notes to turn into a message, ask for feedback on a draft, ask for talking points before a conversation, or just draft a work message with it. Its rules are checked against the adversarial cases in [tests/corporate-communication.md](tests/corporate-communication.md).

## Status

`v1.1.0` adds Corporate Communication. Both skills are public betas for real-world use and feedback. Corporate Communication has been checked against the adversarial cases in [tests/corporate-communication.md](tests/corporate-communication.md), but it has not yet been formally evaluated. The repository does not claim a reliability score or guaranteed improvement.

## License

[MIT](LICENSE)

Created and maintained by [**Achal Jain**](https://github.com/Achal13jain).
