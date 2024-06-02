---
aliases:
  - obsidian-strip-internal-links
tags:
  - "#python"
  - "#software-development"
  - "#developer-tools"
  - "#open-source"

  - "#obsidian"
  - obsidian-plugin
---
# obsidian_strip_internal_links

## obsidian_strip_internal_links usage

## Installation

### Via `pip`

```bash
pip install obsidian_strip_internal_links
```

### From source
To run this program from the code directly, [`python`](https://www.python.org/) and [`poetry`](https://python-poetry.org/) (`pip install poetry`) are required. Clone or download the repository.

To install all the dependencies, use your command line and navigate to the directory where this `README` file is located in. Then run

```bash
poetry install
```

### For development

For development installation perform the [From source](#from-source) installation.

For installing new packages, always run
```
poetry add <pip-package-name>
```
instead of `pip install <pip-package-name>`.

Launch the program either check out the [Execution](#execution) section or use the *Run and Debug*-side panel of VSCode.

If the interpreter of the virtual environment does not show up in VSCode, add it manually. The virtual environments are located in `{cache-dir}/virtualenvs/<venv-name>/Scripts/python.exe` where the [`{cache-dir}`](https://python-poetry.org/docs/configuration/#cache-dir) depends on the operating system (`~/.cache/pypoetry`, `~/Library/Caches/pypoetry` or `C.\Users\%USERNAME%\AppData\Local\pypoetry\Cache`).

## Execution

To execute the program use
```bash
poetry run python -m obsidian_strip_internal_links
```

