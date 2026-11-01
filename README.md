# Kurigram Telegram Bot

<p align="center">
  <strong>Build Telegram bots with confidence, from the first handler to raw MTProto.</strong>
  <br />
  A source-aware skill for Codex, Claude Code, and compatible coding agents.
</p>

<p align="center">
  <a href="https://github.com/blockton/kurigram-telegram-bot/stargazers"><img src="https://img.shields.io/github/stars/blockton/kurigram-telegram-bot?style=for-the-badge&logo=github&label=stars" alt="GitHub stars" /></a>
  <img src="https://img.shields.io/badge/Kurigram-2.2.26-168B8B?style=for-the-badge" alt="Kurigram 2.2.26" />
  <img src="https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Agent%20skill-Codex%20%7C%20Claude-7C3AED?style=for-the-badge" alt="Codex and Claude skill" />
</p>

> [!NOTE]
> Kurigram uses the `pyrogram` import namespace. This skill is pinned to Kurigram **2.2.26**; check your project’s installed version before relying on version-specific APIs.

## What’s inside

- A searchable inventory of the public API, signatures, raw types, and source locations.
- Focused guides for handlers, messaging, Rich Messages, media, lifecycle, and MTProto.
- Runnable bot examples and offline checks that need no Telegram login or live API calls.
- Clear boundaries between documented APIs, raw-only paths, and behavior that still needs verification.

The index is broad; the practical guides focus on workflows where details are easy to get wrong. See [how the inventory is built and what it covers](references/api-inventory.md#inventory-boundary) and the [source/version audit](references/provenance.md).

## Install

Clone this repository into your agent’s personal skills directory. Pick the path your agent reads:

```sh
# Codex
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/blockton/kurigram-telegram-bot \
  "${CODEX_HOME:-$HOME/.codex}/skills/kurigram-telegram-bot"
```

For Claude Code, use `~/.claude/skills/kurigram-telegram-bot`. Agents configured to read a shared `~/.agents/skills` directory can use that location instead. Restart or refresh the agent after installing.

## Use it

Ask your agent to build, debug, or review a Kurigram bot. You can invoke it directly with `$kurigram-telegram-bot`, or let the agent select it automatically for a Kurigram task.

For a direct API lookup from the skill directory:

```sh
python scripts/api_inventory.py RichTextButton
python scripts/api_inventory.py pyrogram.Client.send_rich_message --limit 5
```

## Guides and examples

| If you’re working on… | Start here |
| --- | --- |
| Bot setup, sessions, deployment, or project structure | [Lifecycle and production](references/lifecycle-production.md) |
| Handlers, filters, callbacks, or inline queries | [Handlers and interactions](references/handlers-interactions.md) |
| Text, captions, entities, replies, or edits | [Messaging and formatting](references/messaging-formatting.md) |
| Rich blocks, tables, buttons, or drafts | [Rich Messages](references/rich-messages.md) · [Rich interactions](references/rich-interactions.md) |
| Uploads, downloads, albums, or file IDs | [Media](references/media.md) |
| Payments, stories, business features, or other API domains | [Capabilities](references/capabilities.md) |
| Raw requests, RPC errors, flood waits, or performance | [Raw API and errors](references/raw-errors-performance.md) |
| API symbol and signature search | [API inventory](references/api-inventory.md) |

Starter bots live in [`assets/`](assets/): a minimal `/start`, an owner-bound callback flow, and a Rich Message table. They’re examples to adapt, not production templates.

## Verify offline

With Python and the pinned Kurigram release available:

```sh
uv run --with 'kurigram==2.2.26' python scripts/verify_offline.py
```

This checks imports, signatures, serialization, and selected behavior against fake adapters. It does **not** verify Telegram rendering, account permissions, server acceptance, or live RPC behavior. See the [verification scope](references/examples-testing.md#what-the-checks-establish).

## Design principles

- Keep the project’s chosen Telegram framework; this skill does not migrate bots to Kurigram.
- Check the installed version and real signatures before using version-specific APIs.
- Treat account rights and server capabilities as separate from what a raw constructor can serialize.
- Preserve message entities and callback authorization deliberately.
- Never need bot tokens or a live Telegram session for the included offline checks.

---

<p align="center">
  Built for careful bot work · <a href="https://github.com/kurigram-org/kurigram">Kurigram</a> · <a href="references/provenance.md">Version and provenance</a>
</p>
