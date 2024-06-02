---
aliases:
  - collective
tags:
  - ai
  - artificial-intelligence
  - rust
  - "#ai"
  - "#rust-tool"
  - "#gpt-4"
  - "#docker"
  - "#openai"

  - "#ai-developer"
  - "#adaptive-ai"
  - "#project-management"
---
# collective

[**Discord**](https://discord.gg/CzeXcYU8nC)
[![codecov](https://codecov.io/github/getcollective-ai/collective/branch/main/graph/badge.svg?token=C7HBZAAX3B)](https://app.codecov.io/gh/getcollective-ai/collective)
[<img alt="build status" src="https://img.shields.io/github/actions/workflow/status/getcollective-ai/collective/coverage.yml?branch=main&style=for-the-badge" height="20">](https://github.com/getcollective-ai/collective/actions?query=branch%3Amain)


<img width="1564" alt="image" src="https://user-images.githubusercontent.com/7644264/232889999-7f76cef7-2602-423f-b907-bf943807ece6.png">

An AI developer that evolves to fit your needs.

---
`collective` is an AI developer that adapts to your preferences and biases.
When prompted to create a project, it engages through prompts and questions, improving
its understanding of you. Collective continuously evolves and refines its abilities to support
you—transfering its knowledge between independent projects.

# [📜 Docs](https://github.com/getcollective-ai/docs)

# Running
```zsh
OPENAI_KEY='sk-xxxxxxxxxx' cargo run -p frontend-cli
```

# Keys

- `ENTER` submit an answer
- `TAB` proceed to next step (currently from asking to planning)
- `ESC` exit the program

# Tech Stack

| Component                     | Technology        |
 |-------------------------------|-------------------|
| Base OS                       | macOS/Unix.       |
| Interface                     | tui-rs (vim-like) |
| Isolation                     | docker            |
| Isolation Env (OS)            | ubuntu            |
| Isolation Env (Shell)         | zsh               |
| Data (and preference) storage | mongodb           |
| Core library, executor        | rust              |
| LLM                           | GPT4              |

# MVP

- Learn preferences through Q&A while making a project and
  adapt them to make a separate project (as defined by the user) with minimal input from the user

## Requirements

### Internals

- text-based search engine
    - capable of searching `GitHub`, `crates.io`, `docs.rs`, and `rust-lang.org`
        - only look at `GitHub` repos with the correct license

## Evaluation

- style transfer between projects is apparent
- the assistant is able to make the second project with near minimal assistance
