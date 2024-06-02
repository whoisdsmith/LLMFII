---
tags: ["#chatgpt", "#cli", "#openai", "#python", "#text-generation", "|", "#elia-chat", "#terminal-ui", "#local-models"]
---

# elia_chat

## Description

A powerful terminal user interface for interacting with large language models.

## README

<h1 align="center">
    <img src="https://github.com/darrenburns/elia/assets/5740731/4037b91a-1ad8-4d5b-884d-b3f1b495acf4" width="126px">
</h1>
<p align="center">
  <i align="center">A snappy, keyboard-centric terminal user interface for interacting with large language models.</i><br>
  <i align="center">Chat with Claude 3, ChatGPT, and local models like Llama 3, Phi 3, Mistral and Gemma.</i>
</p>

![elia-screenshot-collage](https://github.com/darrenburns/elia/assets/5740731/75f8563f-ce1a-4c9c-98c0-1bd1f7010814)

## Introduction

`elia` is an application for interacting with LLMs which runs entirely in your terminal, and is designed to be keyboard-focused, efficient, and fun to use!
It stores your conversations in a local SQLite database, and allows you to interact with a variety of models.
Speak with proprietary models such as ChatGPT and Claude, or with local models running through `ollama` or LocalAI.

## Installation

Install Elia with [pipx](https://github.com/pypa/pipx):

```bash
pipx install elia-chat
```

Depending on the model you wish to use, you may need to set one or more environment variables (e.g. `OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, etc).

## Quickstart

Launch Elia from the command line:

```bash
elia
```

Launch a new chat inline (under your prompt) with `-i`/`--inline`:

```bash
elia -i "What is the Zen of Python?"
```

Launch a new chat in full-screen mode:

```bash
elia "Tell me a cool fact about lizards!"
```

Specify a model via the command line using `-m`/`--model`:

```bash
elia -m gpt-4o
```

Options can be combined - here's how you launch a chat with Gemini 1.5 Flash in inline mode.

```bash
elia -i -m gemini/gemini-1.5-flash-latest "How do I call Rust code from Python?"
```

## Running Local Models

1. Install [`ollama`](https://github.com/ollama/ollama).
2. Pull the model you require, e.g. `ollama pull llama3`.
3. Run the local ollama server: `ollama serve`.
4. Add the model to the config file (see below).

## Configuration

The location of the configuration file is noted at the bottom of
the options window (`ctrl+o`).

The example file below shows the available options, as well as examples of how to add new models.

```toml
# the ID or name of the model that is selected by default on launch
default_model = "gpt-4o"
# the system prompt on launch
system_prompt = "You are a helpful assistant who talks like a pirate."
# change the syntax highlighting theme of code in messages
# choose from https://pygments.org/styles/
# defaults to "monokai"
message_code_theme = "dracula"

# example of adding local llama3 support
# only the `name` field is required here.
[[models]]
name = "ollama/llama3"

# example of a model running on a local server, e.g. LocalAI
[[models]]
name = "openai/some-model"
api_base = "http://localhost:8080/v1"
api_key = "api-key-if-required"

# example of add a groq model, showing some other fields
[[models]]
name = "groq/llama2-70b-4096"
display_name = "Llama 2 70B"  # appears in UI
provider = "Groq"  # appears in UI
temperature = 1.0  # high temp = high variation in output
max_retries = 0  # number of retries on failed request

# example of multiple instances of one model, e.g. you might
# have a 'work' OpenAI org and a 'personal' org.
[[models]]
id = "work-gpt-3.5-turbo"
name = "gpt-3.5-turbo"
display_name = "GPT 3.5 Turbo (Work)"

[[models]]
id = "personal-gpt-3.5-turbo"
name = "gpt-3.5-turbo"
display_name = "GPT 3.5 Turbo (Personal)"
```

## Import from ChatGPT

Export your conversations to a JSON file using the ChatGPT UI, then import them using the `import` command.

```bash
elia import 'path/to/conversations.json'
```

## Wiping the Database

```bash
elia reset
```

## Uninstalling

```bash
pipx uninstall elia-chat
```
