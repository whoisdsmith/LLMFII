---
tags:
  - "#developer-tools"
  - "#open-source"

  - "#obsidian"
  - "#note-publishing"
  - "#plugin-development"
---
## Obsidian Publish Notes plugin



A DIY way to publish your Obsidian notes with anyone you want to.



This plugin has a vert technical setup and you will need an [Airtable Account](https://airtable.com/)



## How to install



You can find the docs in my own docs website.



[Publish Notes Docs](https://notes.iamsaravieira.com/notes/oss-obsidian-share-link-docsmd)



## Run locally



```

git clone git@github.com:SaraVieira/obsidian-notes-publish-plugin.git

cd obsidian-notes-publish-plugin

yarn && cd plugin && yarn && cd ../website && yarn && cd ..

yarn dev

```



Please change the [dist of the plugin build](https://github.com/SaraVieira/obsidian-notes-publish-plugin/blob/0.0.1/plugin/esbuild.config.mjs#L30) to where you have your obsidian plugins folder.



## License



MIT

