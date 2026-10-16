# mindcode-plugins-official

The official plugin marketplace for [Mind](https://mindcode.sh)

## Install the marketplace

| Tool | Command |
| --- | --- |
| Mind | `/plugin marketplace add mind-code-ai/mindcode-plugins-official` |
| Claude Code | `/plugin marketplace add mind-code-ai/mindcode-plugins-official` |
| Augment Code | `/plugin marketplace add mind-code-ai/mindcode-plugins-official` |

For Mind, Claude Code and Augment Code, install any plugin listed below:

```
/plugin install butler@mindcode-plugins-official
```

Plugin commands are namespaced by plugin name — the example above adds:

```
/butler:greet Ada
```

## Codex

Register the marketplace and install a plugin with Codex CLI:

```sh
codex plugin marketplace add mind-code-ai/mindcode-plugins-official --ref main
codex plugin add copywriting@mindcode-plugins-official
```

Replace `copywriting` with any plugin below. To inspect or update the catalog:

```sh
codex plugin list --marketplace mindcode-plugins-official --available --json
codex plugin marketplace upgrade mindcode-plugins-official
```

Start a new Codex session after installing. Ask Codex to use the installed
skill, for example “Use the copywriting skill to rewrite this landing page”.
Butler exposes its greeting as the `greet` skill in Codex; its existing slash
command remains available in the other clients. Skills that need an external
tool or design canvas still require that capability in the host environment.

Codex reads `.agents/plugins/marketplace.json` and each plugin's
`.codex-plugin/plugin.json`, which references the shared `skills/` directory.
These files follow the [Codex plugin packaging documentation](https://developers.openai.com/plugins/build/plugins).

## Plugins

| Plugin | Description |
| --- | --- |
| [butler](plugins/butler) | A greeting plugin to learn the basics |
| [fme](plugins/fme) | Author, edit and validate FME workspaces (.fmw), run jobs on FME Flow, and write PythonCaller scripts across FME versions |
| [copywriting](plugins/copywriting) | Write, edit and de-AI marketing copy: page copy, line-by-line editing, humanizing AI-sounding text, and classic advertising principles |
| [figma](plugins/figma) | Work a design file: radiographs, motion, camera moves, interface craft, component handoff, color tokens, audits, UI states, design review, and usability guides |
| [blog](plugins/blog) | Write, review, and tighten engineering blog posts so a developer would send the piece to a teammate |

## Plugin structure

Mind's native convention is `.mind-plugin/` — it takes precedence when
present. For cross-tool compatibility, plugins in this marketplace also carry
`.claude-plugin/` and `.augment-plugin/` copies of the same manifest:

```
butler/
├── .mind-plugin/plugin.json      # Mind (native, wins when present)
├── .claude-plugin/plugin.json    # Claude Code compatibility
├── .augment-plugin/plugin.json   # Augment Code compatibility
├── commands/                     # slash commands (markdown)
├── skills/                       # skills (SKILL.md directories)
├── agents/                       # agent personas
└── hooks/ · mcp/                 # hooks and MCP server configs
```

`plugin.json` is the same shape everywhere:

```json
{
  "name": "butler",
  "description": "A greeting plugin to learn the basics",
  "version": "1.0.0",
  "author": {
    "name": "Your Name"
  }
}
```

The marketplace itself is declared once per convention
(`.mind-plugin/marketplace.json` and compatibility copies):

```json
{
  "name": "mindcode-plugins-official",
  "owner": { "name": "thebrightondev" },
  "plugins": [
    { "name": "butler", "source": "./plugins/butler" }
  ]
}
```

## Contributing a plugin

1. Add a directory under `plugins/<your-plugin>/` with the three manifest
   copies and your components (`commands/`, `skills/`, …).
2. Register it in all three `marketplace.json` files (keep them identical).
3. Add a `.codex-plugin/plugin.json` with `skills: "./skills/"` and register
   the plugin in `.agents/plugins/marketplace.json` with source and policies.
   Provide a skill equivalent for command-only workflows.
4. Verify manifests and Codex discovery/install behavior, then open a PR.

Full documentation: <https://mindcode.sh/docs/en/plugins>
