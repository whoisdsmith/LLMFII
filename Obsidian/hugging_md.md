---
aliases:
  - hugging-md
tags:
  - obsidian-plugin
  - plugin
  - huggingface
  - "#huggingface"
  - "#text-generation"
  - "#software-development"
  - "#open-source"

  - "#obsidian-plugin"
  - "#text-inference"
  - "#svelte"
---
# 🤗📝 Hugging.md

HuggingFace assisted Obsidian plugin, bundling text inferences e.g. summarization, paraphrasing or other text generation available in HuggingFace as commands. Currently work-in-progress and haven't sent to Obsidian community plugins.

**Current Feature(s)**

-   Summarize selected text (as proof-of-concept)
    <img src="./assets/preview-hugging-md.gif" width="640" height="486" />
-   Token classification with selected text
-   Currently, experimenting on Svelte component and injecting to markdown component.

## Installation

-   Clone this repository to vault `.obsidian/plugins` directory
-   `pnpm install` to install dependencies
-   `pnpm build` to build
-   Refresh installed community plugins and enable Hugging.md

For those who use [Warp.terminal](https://www.warp.dev/) you can copy workflow `push-to-local-sample.yaml` to new one, change parameters and run workflow to push build files to vault plugin folder.
