---
tags:
  - "#chatgpt"
  - "#plugin"
  - "#open-source"
  - "#api"
  - "#archive"

  - "#web-rewind"
  - "#website-snapshots"
  - "#vercel-functions"
---
<p align="center">
  <img
    src=".github/logo.png"
    align="center"
    width="100"
    alt="Web Rewind"
    title="Web Rewind"
  />
  <h1 align="center">Web Rewind</h1>
</p>

<p align="center">
  ChatGPT plugin that allows you to see how websites looked like in the past.
</p>


## 🚀 Concept

Web Rewind is a plugin for [ChatGPT](https://chat.openai.com) that allows you to see how websites looked like in the past. Internally, it uses [Archive.org](https://archive.org) to retrieve the snapshots of the websites with [FlashAPI](https://apiflash.com/dashboard/query_builder) to enhance the quality of the images presented in the chat UI.

## 🦾 How it works

Web Rewind is composed by the OpenAI plugin architecture, which is composed by a manifest, an OpenAPI specification and one API.

```
/.well-known
  ai-plugin.json
/api
  get-wayback-url.py
.gitignore
openapi.yaml
```

To make the plugin really fast, I decided to use only one endpoint to retrieve the snapshots of the websites with the URL and the date as parameters. Also, I use the power of [Vercel Serverless Functions](https://vercel.com/docs/serverless-functions/introduction) to make the endpoint faster.

## 🤲 Contributing

Web Rewind is an open source project.

If you want to be the author of a new feature, fix a bug or contribute with something new.

Fork the repository and make changes as you like. [Pull requests](https://github.com/360macky/project-name/pulls) are warmly welcome.

## 📃 License

Distributed under the MIT License.
See [`LICENSE`](./LICENSE) for more information.

