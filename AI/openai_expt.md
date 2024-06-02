---
aliases:
  - openai-expt
tags:
  - openai-api
  - python
  - image-generation
  - "#python"
  - "#openai"
  - "#image-generation"
  - "#generative-ai"

  - "#dalle"
  - "#image-prompt"
---
# Playing with OpenAI APIs

[![python](https://img.shields.io/badge/Python-3.10-3776AB.svg?style=flat&logo=python&logoColor=white)](https://www.python.org)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)
[![Checked with mypy](http://www.mypy-lang.org/static/mypy_badge.svg)](http://mypy-lang.org/)
[![pydocstyle](https://img.shields.io/badge/pydocstyle-enabled-AD4CD3)](http://www.pydocstyle.org/en/stable/)
[![License: GPLv3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

## DALL-E

Generate images for example prompts.

```bash
❯ python dalle.py examples
Generating images for 'A man standing on a bridge in California.'
100%|█████████████████████████████████████████████████████████████████████████████████| 3/3 [00:00<00:00, 6329.43it/s]
Generating images for 'A cat waving to her mom.'
100%|█████████████████████████████████████████████████████████████████████████████████| 3/3 [00:00<00:00, 8671.89it/s]
Generating images for 'Elvis jumping out of a cake.'
100%|████████████████████████████████████████████████████████████████████████████████| 3/3 [00:00<00:00, 10745.44it/s]
Generating images for 'Golden retriever riding the space shuttle to the moon.'
100%|█████████████████████████████████████████████████████████████████████████████████| 3/3 [00:00<00:00, 9467.95it/s]
```

(Note that DALL-E was specifically trained with some precautions against producing identifiable images of celebrities, e.g. Elvis.)

<center>
<img src="dalle-results/a-man-standing-on-a-bridge-in-california_1024x1024/image-002.jpeg" alt="A man standing on a bridge in California." width="23%">
<img src="dalle-results/a-cat-waving-to-her-mom_1024x1024/image-000.jpeg" alt="A cat waving to her mom." width="23%">
<img src="dalle-results/elvis-jumping-out-of-a-cake_1024x1024/image-000.jpeg" alt="Elvis jumping out of a cake." width="23%">
<img src="dalle-results/golden-retriever-riding-the-space-shuttle-to-the-moon_1024x1024/image-002.jpeg" alt="Golden retriever riding the space shuttle to the moon." width="23%">
</center>

Or run with new prompts.

```bash
❯ ./dalle.py generate "a baby duck in a tea cup on a table" --n 3
Generating images for 'a baby duck in a tea cup on a table'
100%|███████████████████████████████████████████████████████████████████████████████████| 3/3 [00:20<00:00,  6.69s/it]
```

<center>
<img src="dalle-results/a-baby-duck-in-a-tea-cup-on-a-table_1024x1024/image-000.jpeg" alt="a baby duck in a tea cup on a table (img 1)" width="30%">
<img src="dalle-results/a-baby-duck-in-a-tea-cup-on-a-table_1024x1024/image-001.jpeg" alt="a baby duck in a tea cup on a table (img 2)" width="30%">
<img src="dalle-results/a-baby-duck-in-a-tea-cup-on-a-table_1024x1024/image-002.jpeg" alt="a baby duck in a tea cup on a table (img 3)" width="30%">
</center>

I played around with requesting different styles for the same prompt. The prompt was **"A computer programmer in the style of \<insert artist\>."**

**Claude Monet**

<center>
<img src="dalle-results/a-computer-programmer-in-the-style-of-claude-monet_1024x1024/image-000.jpeg" alt="A computer programmer in the style of Claude Monet (img 1)" width="25%">
<img src="dalle-results/a-computer-programmer-in-the-style-of-claude-monet_1024x1024/image-001.jpeg" alt="A computer programmer in the style of Claude Monet (img 2)" width="25%">
<img src="dalle-results/a-computer-programmer-in-the-style-of-claude-monet_1024x1024/image-002.jpeg" alt="A computer programmer in the style of Claude Monet (img 3)" width="25%">
</center>

**Vincent van Gogh**

<center>
<img src="dalle-results/a-computer-programmer-in-the-style-of-vincent-van-gogh_1024x1024/image-000.jpeg" alt="A computer programmer in the style of Vincent van Gogh (img 1)" width="25%">
<img src="dalle-results/a-computer-programmer-in-the-style-of-vincent-van-gogh_1024x1024/image-001.jpeg" alt="A computer programmer in the style of Vincent van Gogh (img 2)" width="25%">
<img src="dalle-results/a-computer-programmer-in-the-style-of-vincent-van-gogh_1024x1024/image-002.jpeg" alt="A computer programmer in the style of Vincent van Gogh (img 3)" width="25%">
</center>

**Jackson Pollock**

<center>
<img src="dalle-results/a-computer-programmer-in-the-style-of-jackson-pollock_1024x1024/image-000.jpeg" alt="A computer programmer in the style of Jackson Pollock (img 1)" width="25%">
<img src="dalle-results/a-computer-programmer-in-the-style-of-jackson-pollock_1024x1024/image-001.jpeg" alt="A computer programmer in the style of Jackson Pollock (img 2)" width="25%">
<img src="dalle-results/a-computer-programmer-in-the-style-of-jackson-pollock_1024x1024/image-002.jpeg" alt="A computer programmer in the style of Jackson Pollock (img 3)" width="25%">
</center>

**"DALL-E" (itself)**

<center>
<img src="dalle-results/a-computer-programmer-in-the-style-of-dalle_1024x1024/image-000.jpeg" alt="A computer programmer in the style of DALL-E (img 1)" width="25%">
<img src="dalle-results/a-computer-programmer-in-the-style-of-dalle_1024x1024/image-001.jpeg" alt="A computer programmer in the style of DALL-E (img 2)" width="25%">
<img src="dalle-results/a-computer-programmer-in-the-style-of-dalle_1024x1024/image-002.jpeg" alt="A computer programmer in the style of DALL-E (img 3)" width="25%">
</center>
