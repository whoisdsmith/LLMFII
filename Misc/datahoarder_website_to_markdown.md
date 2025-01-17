---
aliases:
  - datahoarder-website-to-markdown
tags:
  - "#open-source"
  - "#data-pipelines"
  - "#document-parsing"

  - "#web-scraping"
  - "#bash-script"
  - "#markdown-conversion"
---
# 💾 datahoarder-website-to-markdown 🏴‍☠️ 

### Description ⚡
This bash script takes cookies and a list of forum/webpage indexes as input, then it scrapes all urls from the indexes and download the associated pages as single html. All html files are converted to **lightweight** markdown pages (~15-20Kb), then they are trimmed (the **sed** parameters for trimming must be edited because they are different from website to website) and saved in folders called as the name associated with the index (read the list at the top of the script). All the scraped contents are uploaded to a remote git repository (you can store the git credentials by configuring git, so you can make the full process automatic).
- forums with "click Like to show the thread" are supported by this script
- if there is a connection error or the website blocks the scraping, the script can be resumed without losing the previously scraped files
- deleted files are moved to trashbin (I don't use **rm** but **gio trash**)
- the script must be edited in order to be correctly executed

### Screens 🖼
![image](https://i.imgur.com/gDKXN9T.png)

### Dependences 📜
- [html2md](https://github.com/suntong/html2md)
- [crawley](https://github.com/s0rg/crawley)
- curl
- rsync
- git
