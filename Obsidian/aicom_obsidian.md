---
aliases:
  - aicom-obsidian
tags:
  - "#ai"
  - "#llm"
  - "#obsidian"
  - "#plugin"
  - "#llama"

  - "#ai-companion"
  - "#local-ai"
  - "#ai-plugin"
---
# AI Companion Obsidian Plugin

This is an AI Companion plugin made for Obsidian (https://obsidian.md).
It uses locally maintained LLama-2 AI model served via
https://github.com/skycover/aicom-llama.cpp server.

You may start conversation inside any document by clicking on a robot icon
in a toolbar. All text before cursor (or only the selected text if any) will be
threated as a prior conversation and the inferenced answer will be typed after
your last sentence.

![AICom demo](https://github.com/skycover/aicom-obsidian/blob/master/aicom-demo.gif?raw=true)

Special marking rules for conversation document:
```
==Params==
Optional section to place metaparameters if you wish to override settings.
NB. Currently collected, but not evaluated.

==System==
Optional section to place the system prompt here if you wish to override settings.

==User==
Your question here.

==AICom==
AI answer

==User==
...and so on.
```

You may use multiline text between the separators.
Don't forget newline before each separator but first.

The separators for User and AICom are inserted automatically. If you need not in
system prompt or parameters override, you may start conversation without any
separators at all.

You are free to edit any text before next query.

You a free to switch to other document tab, while inference in progress.

If you wish to stop inference just click robot icon again.

Look at "AICom: status NNNN PPP" string in a status bar,
where NNNN is a submitted token count and PPP is generated token count
for current inference.

NB. At the border of a context window of your downloaded AI model the inference
may work unexpectedly. So if model behave strange, check the status bar numbers.

## Install instructions
### Server
AICom needs to connect to the local AI server (it may be also installed on
a different computer and accessed via network).

Follow instructions in https://github.com/skycover/aicom-llama.cpp to setup
your own AI brain.
### Plugin
Clone this repository inside the plugins directory of your Obsidian vault:
```
cd Vault/.obsidian/plugins
git clone https://github.com/skycover/aicom-obsidian.git
```
Enable plugin in Obsidian settings.

Check the plugin Settings page.

Open a new document, write something and click on a robot icon.

The inference may need some time to load model into memory.
