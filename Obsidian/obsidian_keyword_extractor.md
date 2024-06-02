---
aliases:
  - Obsidian-keyword-extractor
tags:
  - obsidian-plugin
  - python
  - nlp
  - "#nlp"
  - "#natural-language-processing"
  - "#document-parsing"
  - "#information-retrieval"

  - "#obsidian"
  - "#note-taking"
  - "#rake-algorithm"
---
# Obsidian-keyword-extractor

#### Use NLP Rake algorithm to tag automatically Obsidian note files and link ideas together easily.

Obsidian is a knowledge base and note-taking software application that operates on Markdown files. It allows users to make internal links for notes and then to visualize the connections as a graph. It is designed to help users organize and structure their thoughts and knowledge in a flexible, non-linear way. Obsidian is popular among writers, researchers, academics, and other professionals who need a flexible and powerful note-taking tool. Website: https://obsidian.md/

# Goal of this project:
Remove the time spent by the user to tag and create connections manually between each notes.

# How does it work?
1. loop through each notes (Obsidian stores notes as markdown files, on the local hard drive)
2. extract top 20 keywords from each note using the Rake NLTK algorithm
3. backup the original note in another folder
4. add the keywords as hashtags on top of the note


Example of linked notes in a graph view in Obsidian. This script creates the link automatically based on the note's content
![image](https://user-images.githubusercontent.com/81629213/225636257-76c594d2-ab75-4fe1-846e-c8a470a939b3.png)
