---
aliases:
  - obsidianURLchecker
tags:
  - obsidian-plugin
  - python
  - cli
---
# Obsidian URL Checker

Obsidian URL Checker is a really simple script that scans your whole vault (with the exception of .obsidian and .trash directories) and searches each line in each file for urls.

For every URL it finds, it uses the requests package to check the status and if the URL is not reachable it logs a line in a file at the root of your vault.


### Usage Instructions

The only command line parameter you need to supply, is the path to your vault

```commandline
$ obsidianURLchecker \home\Obsidian\Vault
```

Please note that the script will override the log file each time it runs. I did it this way because I have no use for keeping history of the runs. The change to keep the file and appending each run is relatively simple.

### ToDo

Add the option of supplying the log file location and name

### Disclaimer

This script is offered as is. Feel free to do what you want with it :-)  
