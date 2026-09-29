<p align="center">
  <img src="skills/client-judgment/assets/icon.svg" width="96" height="96" alt="Unsaid Rules icon">
</p>

<h1 align="center">Unsaid Rules</h1>

<p align="center">
  <strong>Clear client communication when delivery facts are messy.</strong>
</p>

<p align="center">
  <img alt="Version 1.0.0" src="https://img.shields.io/badge/version-1.0.0-2EC9B0">
  <a href="LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/license-MIT-6C63FF"></a>
</p>

**Client Judgment** is an agent skill for drafting and reviewing client-facing software delivery messages. It keeps the message grounded without hiding limitations or promising work that was never agreed.

## What it helps with

- Readiness and sign-off questions
- Delays, dependencies, and incidents
- Scope changes and handovers
- Clear ownership without invented deadlines
- Honest pushback when the requested answer is not supported by the facts

## Install

Choose either the Claude Code plugin or the standalone skill. Installing both copies in Claude Code can make the same skill appear twice.

### Claude Code plugin marketplace

In Claude Code, open **Manage Plugins**, select **Marketplaces**, choose **Add**, and enter:

```text
https://github.com/Achal13jain/unsaid-rules
```

Adding the marketplace only makes its catalog available. After it is added, find **Unsaid Rules** in the plugin list and install it.

The same two steps from a terminal are:

```bash
claude plugin marketplace add Achal13jain/unsaid-rules
claude plugin install unsaid-rules@unsaid-rules
```

Invoke the marketplace-installed skill as:

```text
/unsaid-rules:client-judgment
```

### Direct skill installation

With the Skills CLI:

```bash
npx skills add Achal13jain/unsaid-rules --skill client-judgment
```

Add `-g` for a global installation. The installer can configure Claude Code, Codex, and other tools that support the Agent Skills format.

Or copy `skills/client-judgment` into your tool's project skill directory:

| Tool | Project destination | Invoke explicitly |
| --- | --- | --- |
| Claude Code | `.claude/skills/client-judgment/` | `/client-judgment` |
| Codex | `.agents/skills/client-judgment/` | `$client-judgment` |

See the [portability guide](skills/client-judgment/references/portability.md) for invocation examples.

For Claude Code, use either `/unsaid-rules:client-judgment` from the plugin or `/client-judgment` from the standalone skill. If one copy is already installed, remove or disable it before switching installation methods.

## Use it

```text
Use client-judgment. The client asks whether the site is ready for prospect interviews. The inquiry form is disconnected, legal pages still contain placeholders, and mobile checks passed on only two phones. Draft a short, honest reply. No repair date has been agreed.
```

It works from three simple distinctions:

- **Facts:** what was implemented, tested, deployed, or accepted
- **Commitments:** what the sender has agreed or is authorized to promise
- **Next steps:** what can reasonably be proposed without presenting it as completed or scheduled

## Status

`v1.0.0` is a public beta for real-world use and feedback. The repository does not claim a reliability score or guaranteed improvement.

## License

[MIT](LICENSE)

Created and maintained by [**Achal Jain**](https://github.com/Achal13jain).
