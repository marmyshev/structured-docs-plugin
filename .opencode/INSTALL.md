# Installing Structured Docs for OpenCode

For OpenCode 2.x, add the package to the `plugins` array in your global or project `opencode.json`.

```json
{
  "plugins": ["structured-docs@git+https://github.com/marmyshev/structured-docs-plugin.git"]
}
```

You can also add the package from the terminal.

```sh
opencode plugin add github:marmyshev/structured-docs-plugin
```

For OpenCode 1.18.29 and later in the 1.x series, add the package to the `plugin` array in your global or project `opencode.json`, then restart OpenCode.

```json
{
  "plugin": ["structured-docs@git+https://github.com/marmyshev/structured-docs-plugin.git"]
}
```

Restart OpenCode after editing the config. The plugin registers the `sd-docs` skill and `/sd-docs` command.

## Pin a revision

Append `#` and a Git tag or full commit SHA to the package URL. Replace `REF` with the tag or commit you want to install.

```json
{
  "plugins": ["structured-docs@git+https://github.com/marmyshev/structured-docs-plugin.git#REF"]
}
```

Use `plugin` as the config key on OpenCode 1.x, and restart OpenCode after changing the config.

## Local development

Point OpenCode at the absolute path to your checkout.

```json
{
  "plugins": ["/path/to/structured-docs-plugin"]
}
```

Use `plugin` on OpenCode 1.x. If you open the checkout as an OpenCode project, OpenCode discovers `.opencode/plugins/structured-docs.js` automatically.
