---
tags: ["#command-line", "#developer-tools", "#cli", "#api", "#python", "|", "#natural-language-processing", "#terminal-commands", "#termhand"]
---

# Termhand

## Description

A command-line tool that generates terminal commands from natural language prompts.

## README

# TermHand

TermHand is a command-line tool that generates terminal commands from natural language prompts.

## Installation

Install from [PyPI](https://pypi.org/project/TermHand):

```sh
pip install termhand
```

## Usage

To use TermHand, first ensure you have set up your API key. Create a configuration file at `~/.config/termhand/termhand_config.ini` with the following content:

```ini
[termhand]
api_key = your_api_key_here
```

You can get an API Key from the [Google AI Studio](https://aistudio.google.com/app/apikey)

Then, use TermHand from the command line:

```sh
th "How do I create a new folder with the name test?"
```

## Development

Clone the repository and install the dependencies:

```sh
git clone https://github.com/yourusername/termhand.git
cd termhand
pip install -e .
```
