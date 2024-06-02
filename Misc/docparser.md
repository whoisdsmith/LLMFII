---
aliases:
  - docparser
tags:
  - "#python"
  - "#document-parser"
  - "#docx"

  - "#text-extraction"
  - "#python-package"
---
[![Python Version](https://img.shields.io/badge/python-3.7+-blue)](https://www.python.org/downloads/release/python-370/)
![Tests](https://github.com/has-abi/docparser/actions/workflows/test.yml/badge.svg)
[![codecov](https://codecov.io/gh/has-abi/docparser/branch/main/graph/badge.svg?token=4AL385JEH9)](https://codecov.io/gh/has-abi/docparser)

# What is docparser?
docparser is python package that extract text form a DOCX document.

## Installation

```bash
pip install python-docparser
```

## Usage

```python
from docparser import parse 

document = parse("your_docx_document")
print(document.content)
```
