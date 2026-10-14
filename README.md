# Media.io CLI

Agent skills that drive the [Media.io](https://www.media.io/ai/home) CLI from
Codex, Claude Code, and Cursor: discover models and workflows, generate images
and videos, and download the results.

This README documents the `media-io-cli` CLI plugin, displayed as **Media.io CLI**.
The separately installable `media-io` source package, displayed as **Media.io**,
lives in [media-io/plugin-mcp](https://github.com/media-io/plugin-mcp) and
does not install or invoke the local CLI.

## Install

Install and sign in to the Media.io CLI first:

```bash
npm install -g @mediaio/cli
mediaio auth login
```

### Codex

```bash
codex plugin marketplace add media-io/plugin-cli
codex plugin add media-io-cli@wondershare-media-io-cli
```

The CLI marketplace is **Wondershare Media.io CLI** (`wondershare-media-io-cli`).
The separate MCP marketplace is `wondershare-media-io`, with plugin `media-io`.
The two packages can coexist without sharing a marketplace registration.
If Git marketplace installation is unavailable, use the CLI setup script's personal marketplace fallback.

After installation, `mediaio upgrade codex` updates the CLI binary and this CLI
plugin, not the MCP plugin. Reinstall this CLI plugin when migrating an old
installation named `media-io`; do not remove that identity blindly because it
now belongs to MCP.

### Cursor

Install the shared Media.io skill package for Cursor:

```bash
npx skills add media-io/skills -g --agent cursor
```

### Claude Code

Install this repository as a plugin and point the host at `.claude-plugin/`.

The Claude marketplace is also `wondershare-media-io-cli`. The CLI setup script
uses direct `media-io/skills` installation for Claude Code instead.

For an internal source checkout, use `plugin-cli-main/` as the plugin root.

The plugin never installs or repairs the CLI for you — make sure `mediaio` is
already on your `PATH`.

## Skills

- **`mediaio-generate`** — discover models, workflows, and effects, submit a
  generation job, wait for it, and download the result files.

## Layout

| Path | Purpose |
|---|---|
| `.agents/plugins/marketplace.json` | Codex marketplace, `wondershare-media-io-cli` |
| `.codex-plugin/plugin.json` | Codex manifest |
| `.claude-plugin/marketplace.json` | Claude marketplace, `wondershare-media-io-cli` |
| `.claude-plugin/plugin.json` | Claude Code manifest |
| `skills/` | Shared skill package for Codex, Claude Code, and Cursor |

This directory is the complete CLI plugin source root. The public
`media-io/plugin-cli` snapshot places its contents directly at the repository root.
The internal parent repository's `deploy/`, `tools/`, `catalog/`, and sibling
`plugin-mcp-main/` are never included.

Every release keeps both plugin manifests and the shared skills on the same
version so the plugin hosts and direct skill installs use the same snapshot.

## Links

- Product: <https://www.media.io/ai/home>
- CLI: <https://www.npmjs.com/package/@mediaio/cli>
- Terms of Service: <https://www.media.io/terms-of-service.html>
- Privacy Policy: <https://www.media.io/privacy.html>

## License

MIT — see [LICENSE](LICENSE).
