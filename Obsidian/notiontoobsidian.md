---
tags:
  - "#python"
  - "#software-development"
  - "#developer-tools"
  - "#open-source"

  - "#notion"
  - "#obsidian"
  - "#migration-tool"
---
# Notion to Obsidian Migration Tool

A simple tool which migrates all your notion notes to be obsidian ready.

## Overview

It performs the following actions:

1. Removes all UUIDs present on file names, and it's references within other files
2. Converts all notion-database properties present in each file into YAML front-matter
3. Move all non-note attachments into a single folder
4. Re-organizes all your notes from folder-structure to a single folder
5. Create nested tags based on the sub-folder structure extracted from file re-organization from previous step
6. Resolve all internal link references between files

## Instructions

1. Export notion data using 'Export Content' option.
    - Use 'Markdown & CSV' as format
    - Enable 'Create folders for sub-pages'
2. Save and unzip till you see your notes. Keep the location handy
3. Install Python with version >= 3.9
4. Download this project as zip
5. Create a `config.ini` file in `resources` folder using `config-template.ini`
6. Run `main.py`

## Note

1. Attachments section has only been tried for images where screenshots were embedded into notes

## Issues

1. If a `tags` property is already present in a note's YAML front-matter, this tool will not add to it but instead create a new
   property.