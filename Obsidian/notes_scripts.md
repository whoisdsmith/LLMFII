---
aliases:
  - notes-scripts
tags:
  - "#python"
  - "#software-development"
  - "#developer-tools"

  - "#note-management"
  - "#obsidian"
  - "#roam-research"
---
# notes-scripts
Scripts for organizing and reformatting notes, including a number of utilities
for migrating from Roam to Obsidian.

**Use at your own risk. You should have a backup of your notes anyway, but it's
a good idea to back them up before running scripts on them.**

<!-- BEGIN DESCRIPTION TABLE -->
| Name                        | Description                                                                                                                                                                                                                                                                                                                                                         |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| date_changer.py             | Converts from the Roam format of January 1st, 2000 to a format of 2020-01-01                                                                                                                                                                                                                                                                                        |
| day_to_full.py              | Converts daily note of the format YYYY/MM - MMMM/DD.md to YYYY/MM - MMMM/YYYY-MM-DD.md                                                                                                                                                                                                                                                                              |
| firebase_download.py        | Downloads firebase images from roam to a local directory and fixes links                                                                                                                                                                                                                                                                                            |
| list_empty_pages.py         | Lists and optionally removes any empty notes (or other files)                                                                                                                                                                                                                                                                                                       |
| rename_date_references.py   | Finds roam references (e.g., January 1st, 2020) and replaces them with our daily note format                                                                                                                                                                                                                                                                        |
| roam_mathjax_fix.py         | Roam uses double dollar signs everywhere for math. Obsidian uses single for inline and double for multi-line. This converts any lines with double dollar signs to single dollar signs unless they're the only thing on the line (you were writing multi-line math in Roam)  !!! Back up your notes before running this. It should be pretty safe, but who knows !!! |
| sort_dailies.py             | Sorts daily notes into months, such as 2020-01-01 -> Notes/2020/01 - January/01.md                                                                                                                                                                                                                                                                                  |
| standard_note_import.py     | Imports notes from Standard Notes and converts tags to YAML frontmatter                                                                                                                                                                                                                                                                                             |
| table_cleanup.py            | Cleans up tables in markdown files to have proper spacing                                                                                                                                                                                                                                                                                                           |
| update_description_table.py | Script that generates docs table                                                                                                                                                                                                                                                                                                                                    |
| util.py                     | Common utilities to use in scripts, such as enumerating all notes                                                                                                                                                                                                                                                                                                   |
<!-- END DESCRIPTION TABLE -->
