---
aliases:
  - link-name-from-url
tags:
  - obsidian-plugin
  - "#markdown"
  - "#plugin"
  - "#developer-tools"
  - "#open-source"

  - "#obsidian-plugin"
  - "#markdown"
  - "#url-to-link"
---
# Link Name From URL

This is a plugin for [Obsidian](https://obsidian.md) to help generate Markdown links from raw URLs. This plugin does it by taking the part of the URL and transforming it a little bit.

This plugin was created as an alternative to the [obsidian-auto-link-title plugin](https://github.com/zolrath/obsidian-auto-link-title). The main differnce is that **this plugin doesn't fetch a page** and tries to get the name from the URL. The result heavily depends on the site you trying to use it with. For example, this plugin is useless with **youtube** because their URLs do not contain a name. But it works great with the **GitHub** or **curseforge**, for example. Their URLs contain name and **auto-link-title** is actually getting a lot more of unwanted information than this plugin.

**Example**:  
We paste `https://github.com/AlexRazor1337/link-name-from-url` and it gets converted to the `[Link Name From Url](https://github.com/AlexRazor1337/link-name-from-url)`.

## How to use

- Install the plugin
- Select URL or text with URLs and run `get-link-name-from-url` command

Or you can enable `Auto convert` setting in the plugin settings. It will automatically convert URLs you paste.

## Installation (manual)

- Download [latest release](https://github.com/AlexRazor1337/link-name-from-url/releases/latest/) from the **Releases** tab.
- Copy folder from the archive to your vault plugins folder (`VaultFolder/.obsidian/plugins`).
