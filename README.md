<p align="center">
  <img src="https://github.com/arthurglaizal/quiet-token-bar/releases/download/v1.1.0/quiet-token-bar.gif" alt="Quiet Token Bar demo: the context bar above the Claude Code prompt" width="100%">
</p>

# Quiet Token Bar

> **Your context window in one quiet line, grey until it matters.**

A Claude Code mod that sits above the prompt and shows how full your context is, your session and weekly limits, and a one-click compact button.

It stays neutral by default. A figure only turns orange, then red, when it gets close to its limit.

## What it shows

On desktop, small grey text with real stripes and dots. In the terminal, the same line in characters:

```txt
Context  ▆▆⠿⠿⠿⠿────────────▃   491k of 967k  51%  ≍  │ limit  9%  4%  ∨  ×
```

- **The bar**: what fills the window (system prompt, tools, MCP tools, memory files, skills, messages), then free space and the compaction buffer. Each category has its own pattern, so it reads without color.
- **The fill**: tokens used against the point where auto-compaction runs, and the percentage.
- **Compact**: runs `/compact` for you, as if you had typed it.
- **Limits**: your 5-hour session and weekly usage. Hover for the reset time.
- **Details**: the chevron unfolds each category's tokens and share.
- **Close**: hides the bar. `/quiet-token-bar` brings it back.

Everything is grey until a figure reaches 70% (orange), then 90% (red). The figures come from the same breakdown `/context` draws, refreshed after each turn.

## Install

```sh
claude plugin marketplace add arthurglaizal/quiet-token-bar
claude plugin install quiet-token-bar@arturo-mods
```

Start a new session and the bar appears. To update later: `claude plugin update quiet-token-bar@arturo-mods`. To try it without installing, clone the repository and run `claude --plugin-dir ./quiet-token-bar`.

Installed it as Compact Token Bar, before 1.1.0? Remove it first with `claude plugin uninstall compact-token-bar@arturo-mods`.

## Limitations

- Needs Claude Code 2.1.287 or later. An update can change the mod API.
- Session and weekly limits need a Claude subscription, and show after the first response.
- While Claude is answering, Compact waits for the answer to end.

## What it runs and keeps

- **No network requests.** The figures come from Claude Code itself. Nothing is sent anywhere.
- **One command, only on click.** The compact button runs `/compact`. The mod never compacts on its own.
- **Two values kept on your machine**: whether you closed the bar, and the last limits seen, to show them before the first response.

## Repository structure

```txt
quiet-token-bar/
├── README.md
├── LICENSE
├── .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── hooks/
│   ├── hooks.json
│   └── register.tsx
├── types/index.d.ts
└── tests/quiet-token-bar.test.tsx
```

Run the checks with `claude plugin validate .` and `claude plugin test .`.

## Credits

Built on [context-bar](https://github.com/hamzafer/claude-code-mods) by Hamza Zafar (MIT), redesigned around a quieter, single-line layout.

## Quiet mods

<p align="center">
  <img src="https://github.com/arthurglaizal/quiet-model/releases/download/v2.0.0/quiet-mods.png" alt="Quiet Token Bar and Quiet Model stacked above the Claude Code prompt" width="100%">
</p>

The Quiet mods share one design: grey by default, color only when something needs you. They stack neatly above the prompt.

| Mod | Description |
| --- | --- |
| [Quiet Model](https://github.com/arthurglaizal/quiet-model) | Pick the model and effort in one quiet grey row. Or let Magic Router choose for each message. |
| [Quiet Cost](https://github.com/arthurglaizal/quiet-cost) | What each reply cost, in one quiet grey line under it: an estimated price, the time and the tokens, and more figures you pick. |

## Support

If you find my work useful, you can [buy me a coffee](https://ko-fi.com/arturo_ux) ☕️

## License

MIT — see [LICENSE](LICENSE).
