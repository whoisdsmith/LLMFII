---
aliases:
  - obsidian-libllm
tags:
  - obsidian-plugin
  - obsidian
  - llm
  - "#llm"
  - "#plugin"
  - "#obsidian"
  - "#api"
  - "#prompt-generation"

  - "#obsidian-plugin"
  - "#templater"
  - "#pkm"
---
# Obsidian LibLLM

LLM Utility functions for the [Obsidian](https://obsidian.md/) pkm.

## Install

1. Install the plugin
    ```
    cd <path to your obsidian vault>/.obsidian/plugins
    git clone https://github.com/carlsverre/obsidian-libllm.git
    ```

2. Restart Obsidian
3. Enable plugin in settings
4. Configure plugin

## Commands

### Prompt Generation

When generating a prompt in commands, LibLLM will try each of the following methods in order:

1. Use the current selection as the prompt
2. Select the current line and all previous non-empty lines as the prompt

### LibLLM: Complete

This command will generate a prompt (see Prompt Generation above) and send it to the default LLM for completion and insert the result in the current editor immediately following the current cursor position or selection.

### LibLLM: Complete with instructions

This command will prompt the user for instructions in a modal, and then combine those instructions with a generated prompt (see Prompt Generation above). This will be sent to the default LLM for completion and the result will be inserted in the current editor immediately following the current cursor position or selection.

## Plugin API

This plugin is designed to be used from other plugins. You can access it globally within Obsidian via:

```js
const libLLM = app.plugins.getPlugin("obsidian-libllm");

// send the provided prompt to the default LLM and return the completion
libLLM.complete(prompt: string): string

// prompts the user for instructions using a modal, combines that with the
// provided prompt, and then send the result to the default LLM before returning
// the completion
libLLM.completeWithInstructions(prompt: string): string
```

## Using LibLLM from [Templater](https://github.com/SilentVoid13/Templater)

Templater is a very powerful plugin which you can use to run javascript during template generation. When combined with LibLLM this enables powerful custom workflows. Here are some examples:

### Blog post outline generator

```
<%*
const topic = await tp.system.prompt("blog post topic");
const libLLM = app.plugins.getPlugin("obsidian-libllm");
const result = await libLLM.complete(`generate a blog post outline on the following topic formatted as a markdown list: ${topic}`);
%>
Outline:
<% result %>
```

### Complete with file context

```
<%*
const libLLM = app.plugins.getPlugin("obsidian-libllm");
const title = tp.file.title;
const tags = tp.file.tags;
const frontmatter = tp.frontmatter;

const prompt = await tp.system.prompt("Completion prompt");
const context = JSON.stringify({ title, tags, frontmatter });

tR = await libLLM.complete(`
Use the following contextual data if needed:
${context}

Follow these instructions:
${prompt}

Answer formatted as markdown:
`)
%>
```