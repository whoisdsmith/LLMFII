---
aliases:
  - showmd
tags:
  - python

  - markdown
  - "#python"
  - "#developer-tools"
  - "#software-development"

  - "#markdown"
-tools
  - text-formatting
---
# Showmd
Showmd is a simple way to pretty-print markdown text in the terminal. It supports headers, links, lists, text formatting etc. and makes files nice to look at in a terminal environment.

## Requirements:
* `art`
* `beautifulsoup4`
* `colorama`
* `termcolor`

## Usage
`python3 showmd.py myfile.md` - Displays `myfile.md`.

Flags:

* `--a`: Disables ASCII art headers.

## Advanced Features
If header ASCII art is too wide, it will automatically adjust to the width of the terminal if it can. It should also work on Windows and Linux terminals.

## Demo
![Demonstration image](showmd_demo.png)