---
aliases:
  - cli-gpt
tags:
  - cli
  - openai
  - openai-api
  - "#openai"
  - "#gpt"
  - "#ai"
  - "#developer-tools"

  - "#cli-tool"
  - "#command-line-interface"
  - "#tui"
---
# cli-gpt

https://user-images.githubusercontent.com/55558407/223719418-26477b1e-1cf6-4f47-8810-69b665b260dd.mp4

## Usage

Run: `./cli-gpt`

Other options: [commands](./commands.md)

## Configuration

- place custom (system) prompts in `~/.config/cli-gpt/system-prompts/*.txt`
  - to use a custom prompt, see [commands](./commands.md)

## Installation

### Dependencies

- [Gum](https://github.com/charmbracelet/gum) (tui toolkit)
- linxu only (x11): [xclip](https://github.com/astrand/xclip)

### Installing

1. install the dependencies
2. set the `OPENAI_API_KEY` environment variable to [your OpenAI API key](https://help.openai.com/en/articles/4936850-where-do-i-find-my-secret-api-key) (`export OPENAI_API_KEY="<your-api-key>"`)
3. clone this repo & `cd` into it
4. `chmod +x ./cli-gpt`
5. ./cli-gpt
