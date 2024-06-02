---
tags:
  - "#notion"
  - "#markdown"
  - "#github"
  - "#yaml"
  - "#documentation"

  - "#github-action"
  - "#notion-integration"
  - "#markdown-export"
---
# notion-to-markdown-action

[![build-test](https://github.com/ega4432/notion-to-markdown-action/actions/workflows/test.yml/badge.svg)](https://github.com/ega4432/notion-to-markdown-action/actions/workflows/test.yml)
[![Check dist/](https://github.com/ega4432/notion-to-markdown-action/actions/workflows/check-dist.yml/badge.svg)](https://github.com/ega4432/notion-to-markdown-action/actions/workflows/check-dist.yml)
[![auto-merge](https://github.com/ega4432/notion-to-markdown-action/actions/workflows/auto-merge.yml/badge.svg)](https://github.com/ega4432/notion-to-markdown-action/actions/workflows/auto-merge.yml)
[![auto-release](https://github.com/ega4432/notion-to-markdown-action/actions/workflows/auto-release.yml/badge.svg)](https://github.com/ega4432/notion-to-markdown-action/actions/workflows/auto-release.yml)

## Overview

This action converts and downloads pages that exist in Notion's specified database to a markdown files.

## Usage

`.github/workflows/import.yml`

```yaml
name: import

on:
  schedule:
    - cron: '0 0 * * *'

jobs:
  import:
    runs-on: ubuntu-latest
    steps:
      - id: import
        uses: ega4432/notion-to-markdown-action@v0
        env:
          NOTION_API_KEY: ${{ secrets.NOTION_API_KEY }}
          NOTION_DATABASE_ID: ${{ secrets.NOTION_DATABASE_ID }}
        with:
          # Optional
          output_path: some-dir # default: output
          filename_property: slug # default: title
      # You can check output files count
      - run: |
          echo "Exported count: ${{ steps.import.outputs.files_count }}"
```

## Supported

### Runners

- `ubuntu-latest`
- `macos-latest`
- `windows-latest`

### Events

- any

## Environments

| Name                 | Description                       | Required |
| -------------------- | --------------------------------- | -------- |
| `NOTION_API_KEY`     | API key of Notion integrations    | Yes      |
| `NOTION_DATABASE_ID` | Database ID of target Notion page | Yes      |

## Inputs

| Name                | Description                                                                                       | Default  | Required |
| ------------------- | ------------------------------------------------------------------------------------------------- | -------- | -------- |
| `output_path`       | You can specify the directory path to output files.                                               | `output` | No       |
| `filename_property` | You can specify the column of the Notion database to be used as a filename when saving the files. | `title`  | No       |

## Outputs

| Name          | Description                                                   |
| ------------- | ------------------------------------------------------------- |
| `files_count` | You can check the number of files output in subsequent steps. |

## Author

ega4432: [GitHub](https://github.com/ega4432), [Twitter](https://twitter.com/ega4432)

## LICENSE

Copyright © 2023 ega4432.
[MIT License](https://github.com/ega4432/notion-to-markdown-action/blob/main/LICENSE)
