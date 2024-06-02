---
aliases:
  - obsidian-textlint
tags:
  - obsidian-plugin
  - obsidian
  - plugin
---
# Obsidian textlint

This is a plugin for [Obsidian](https://obsidian.md) that integrates [textlint](https://github.com/textlint/textlint), allowing for custmizable rules.

**Note:** To use this plugin, you must first build it. This step is necessary for configuring textlint according to your specific needs.

![Plugin Interface](https://user-images.githubusercontent.com/19975408/217126158-01cea041-3e1a-4b59-9450-dac77336c3a1.png)

See more screenshots and videos [here](https://github.com/hdykokd/obsidian-textlint/issues/1).

## Features

- Utilize textlint with your own set of customized rules.
- Display the Lint Gutter using CodeMirror's built-in functionality.
  - Configurable display settings.
  - Adjustable minimum severity level for showing the lint gutter.
- Show underlines for issues with a tooltip on hover.
- View a list of diagnostics for the active file.
  - Control the minimum severity level to display.
  - Navigate from the list to specific diagnostics with cursor jumps.
- Option to lint when the active file changes.
- Option to lint on file save.
- Option to lint on text changes (experimental).
- Perform fixes if supported by the rule.
- Configure settings to override `.textlintrc` per folder.
  - Read from `.json` file in the vault.
  - Read from code blocks in `.md` file in the vault (see details below).

## Commands

- Display textlint diagnostics.
- Execute textlint linting.

## How to Set Up

1. Install textlint plugins by adding them to `textlint-builder/package.json`.
2. Place your `.textlintrc` configuration in `textlint-builder/textlintrc.json`.
3. Run `npm run build` within the `textlint-builder` directory.
4. Run `npm run build` in the root directory.
5. Create an `obsidian-textlint` directory in `.obsidian/plugins/` within the vault where you want to use the plugin.
6. Copy `main.js`, `styles.css`, `manifest.json`, and `dist` from the root directory to the directory created in step 6.
   - Alternatively, use `scripts/build-and-copy /path/to/.obsidian/plugins`.
7. Open the vault and activate the plugin.

### Configuration: Override `.textlintrc`

You can use the following code block in your `.md` file as an override setting:

````markdown
```json:.textlintrc.json
{
  "rules": {}
}
```
````

![Override Config](https://user-images.githubusercontent.com/19975408/217126182-6bb9a6f1-fe63-43c1-84df-553fa815d942.png)

## Recommendation

To seamlessly incorporate repository changes, remove textlint worker and `.textlintrc` settings from git control by using:

`git update-index --skip-worktree` or `git update-index --assume-unchanged`.

```shell
git update-index --skip-worktree textlint-builder/package.json
git update-index --skip-worktree textlint-builder/textlintrc.json
```
