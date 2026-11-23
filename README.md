# Structured Docs

Organize project documentation by level of abstraction, from goals and business rules to requirements, UI, and technical decisions. The plugin provides the `sd-docs` skill.

## Installation

### Claude Code

Run these commands in Claude Code.

```text
/plugin marketplace add marmyshev/structured-docs-plugin
/plugin install structured-docs@structured-docs-plugin
```

### Codex App

1. Open **Plugins** from the sidebar.
2. Click the arrow next to **Create**, then select **Add marketplace**.
3. Fill in the marketplace fields.

   | Field | Value |
   | --- | --- |
   | Source | `marmyshev/structured-docs-plugin` |
   | Git ref | `main` |
   | Sparse paths | Leave blank |

4. Click **Add marketplace**.
5. Search for **Structured Docs** in the `structured-docs-plugin` marketplace, click **Install**, then restart Codex.

### Codex CLI

Register the marketplace, then install the plugin.

```sh
codex plugin marketplace add marmyshev/structured-docs-plugin
codex plugin add structured-docs@structured-docs-plugin
```

After registering the marketplace, you can also launch `codex`, run `/plugins`, and install **Structured Docs** from the `structured-docs-plugin` marketplace. Restart Codex after installation.

For a non-default profile, use the same `CODEX_HOME` for both commands and when launching Codex.

```sh
CODEX_HOME="$HOME/.codex/profiles/work" codex plugin marketplace add marmyshev/structured-docs-plugin
CODEX_HOME="$HOME/.codex/profiles/work" codex plugin add structured-docs@structured-docs-plugin
```

Both installs include the `sd-docs` skill. Start a new chat and type `$sd-docs` to select it.

### Grok Build CLI (`grok`)

Install Structured Docs directly from this repository. Grok Build loads the plugin from the native `.grok-plugin/plugin.json` manifest.

```sh
grok plugin install marmyshev/structured-docs-plugin
```

To add it as a marketplace source, use the catalog in `.grok-plugin/marketplace.json`.

```sh
grok plugin marketplace add marmyshev/structured-docs-plugin
grok plugin install structured-docs
```

Both installation paths track the repository. Run `grok plugin update` to pull updates. Start a new Grok Build session after installing to load the `sd-docs` skill.

### OpenCode

Add Structured Docs to the `plugins` array in your global or project `opencode.json`.

```json
{
  "plugins": ["structured-docs@git+https://github.com/marmyshev/structured-docs-plugin.git"]
}
```

On OpenCode 1.x, use the singular key `plugin`. This package supports OpenCode 1.18.29 and later in the 1.x series. Restart OpenCode after changing the config. The plugin registers the `sd-docs` skill and `/sd-docs` command directly.

See the [OpenCode installation guide](.opencode/INSTALL.md) for pinning and local development.
