---
aliases:
  - ObsidianYarn
tags:
  - "#python"
  - "#software-development"
  - "#developer-tools"
  - "#open-source"

  - "#obsidian"
  - "#markdown-generator"
  - "#cli-tool"
---
# ObsidianYarn
Generator Obsidian Markdown files from and to files

Takes data from 'plan.txt' and generates md. files in your Obsidian Vault
Data are stored as into ROWS
Each Rows starts with NAME of note [[Duplicit Notes are Possible]]
... continous with name of links

Programm now supports CUSTOM Templates from template folder. You can modify your template and program generate output in theri format. 

AUTHOR IS CONFIGURABLE IN config/config.py

Files will be generated without CONTENT except NAME and Links
Already created files are not OVERWRITTEN by Script.

Happy Hacking :)

# Install
1. clone repository to your computer
2. copy ALL to Vault Folder
3. modify your plan or 000_index__card
4. Configure config/config.py
5. run via CLI as python script

# DEpendencies
python3.7 and above
Obsidian

# Use via CLI in VAULT 
'python3 write_md.py'

# Use via CLI in VAULT
'python3 write_md.py plan.txt'

# tests


