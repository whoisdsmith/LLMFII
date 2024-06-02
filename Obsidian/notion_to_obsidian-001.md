---
aliases:
  - Notion_to_Obsidian
tags:
  - "#python"
  - "#software-development"
  - "#api"

  - "#notion"
  - "#obsidian"
  - "#note-taking"
---
# Notion_to_Obsidian
An automatic way to move notes from Notion to Obsidian (Create a .md file)

## Why to use it
It is mainly intended for the case where you need to take notes but you can't access your local Obsidian vault.   
So if you have internet access, you can access a specific Notion database, write your notes, and when you get to your Obsidian vault, they will be automatically moved and updated.   <br />
This code is not intended for migrating all notes from Notion to Obsidian, but it is somehow an integration between the two different systems.

![](https://forum.obsidian.md/uploads/default/original/2X/6/663886873dba65def747edf8ebf752a0a8d09db0.jpeg)

All details and instructions can be found on the Notion page:
https://lean-newsboy-e60.notion.site/Notion-to-Obsidian-API-automation-6a008b52e4da4642bd2ec949da6d89fc
   
<br />
<br />

## Notes

- The python script ```Notion_API.py``` should be copied to the same folder where the note will be created.
- If you want to change the style of the resulted notes, you can modeify the function ```createMdFile```