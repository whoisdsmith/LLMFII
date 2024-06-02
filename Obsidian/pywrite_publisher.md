---
tags:
  - "#software-development"
  - "#developer-tools"
  - "#open-source"

  - "#markdown-publishing"
  - "#obsidian-alternative"
  - "#nextjs"
---
# nextjs-obsidian-publish
alternative to Obsidian Publish

codename: *Obsidian.md Pyrite Publisher*

## 🎁 Features
0. interactive node graph
0. callout quote blocks
0. markdown links (no support for wiki links)
0. file tree navigation
0. interactive table of contents
0. markdown images (external and internally hosted)
1. fuzzy site search

## 📷 Screenshots
![pywriter-publisher-04](https://github.com/wchorski/PyWrite-Publisher/assets/33769609/94a5adb9-761a-461c-8e5a-3053fa0323ab)
![pywriter-publisher-03](https://github.com/wchorski/PyWrite-Publisher/assets/33769609/33d9381a-ef53-4787-983a-904163a5ea7f)
![pywriter-publisher-02](https://github.com/wchorski/PyWrite-Publisher/assets/33769609/860c7cc8-1f43-4b3e-9bcf-66d51b9b3d78)
![pywriter-publisher-01](https://github.com/wchorski/PyWrite-Publisher/assets/33769609/13c27627-3330-487d-8f9f-b281e150caf1)

## ⚙ Development Setup
1. copy any notes into `./MarkdownVault/`
2. include file `./MarkdownVault/index.md`
3. npm i
4. npm run init
5. npm run dev

## 🏭 Production Setup
1. copy any notes into `./MarkdownVault/`

```shell
./MarkdownVault/
  - index.md
  - file1.md
  - file2.md
  * folderA/
    - fileA1.md
    - fileA2.md
```

2. include a `./MarkdownVault/index.md` that acts as the glossery of your notes
3. if building with docker
  - `docker compose up -d`
4. else 
  -  `npm run init`
  -  `npm run build`


## 👇 Markdown Tips 
```md
create unique headers per page.
### Dogs 
### Cats ✔

Do not repeate same header on the same page
### Fish 
### Fish ❌ 

even if it's a smaller header
### Birds 
#### Birds ❌
```
> [!warning]
> don't use **links/tags** in headers. It will screw up the "Table of Contents" widget

```md
do NOT use links in headers

## Clean Header ✔
## [bad header](https://www.windows93.net/) ❌
```

>[!warning] all attachments in `./MarkdownVault/_attachments` will all be publicly viewable

```md
keep all attacments in `./MarkdownVault/_attachments/` directory

./MarkdownVault/_attachments/camel.jpg ✔
./MarkdownVault/_attachments/reptiles/lizard.jpg ❌
```

## 🌠 Wishlist 
- [ ] better functioning graph with Pixi.js
- [ ] interactive tag system
