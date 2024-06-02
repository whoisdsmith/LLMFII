---
tags:
  - "#ai"
  - "#gpt-4"
  - "#openai"
  - "#google-bard"
  - "#llm"

  - "#desktop-assistant"
  - "#multi-modal"
  - "#experimental-software"
---
<h1><kbd>⌘ Command</kbd> <kbd>⊞ Windows</kbd></h1>

CommandWindows (<kbd>⌘</kbd> <kbd>⊞</kbd>) is a desktop opeating system copilot based on multi-modal large language model, supporting all-platforms which have application windows.

## Supported Model

- [x] GPT4 Vision from OpenAI (`gpt-4-vision-preview`)
- [x] Gemini Pro Vision from Google (`gemini-pro-vision`)
- [ ] Gemini Nano/Ultra Vision from Google
- [ ] Local Vision Model
  - [ ] Vary-toy

## Features

Preview:

> Help me create a Google doc and write the definition of Blockchain on that

[![CommandWin Test Video](https://img.youtube.com/vi/0nnb4PhPv4k/0.jpg)](https://www.youtube.com/watch?v=0nnb4PhPv4k)

- [x] A digital assistant rather than just software
- [x] Use multi-modal perception to help you operate your computer
- [x] Step by step notification showing
- [ ] Testing on more platforms
- [ ] More detailed device information to LLM
- [ ] Enhanced chat experience with better reply content
- [ ] More interactive operation
- [ ] Convinent shortcuts

## How to use

While an official release is not yet available due to the experimental status, you can still try out this tool by cloning the repository and then running on your system.

```
git clone https://github.com/c0mm4nd/command-windows
cd command-windows
npm i 
npm run start
```

The pre-built releases will be available soon!

## How to build

Simply run
```
npm run make
```

The built file is inside the `make` folder

## Status

Inspired by [SOC](https://github.com/OthersideAI/self-operating-computer) but written in Electron with Javascript. 

Currently, this project is
- actively in development and experimental, not suitable for any production
- welcoming any kind of issues and pull requests!
