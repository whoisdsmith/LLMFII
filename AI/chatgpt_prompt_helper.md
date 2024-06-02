---
aliases:
  - chatgpt-prompt-helper
tags:
  - chatgpt
  - prompt-engineering
  - chrome-extension
---
# ChatGPT Prompt helper
<img src="./assets/icon.png" width="60px" style="margin: auto; display: block" />

This Browser extension is going to prower chatGPT with awesome chatgpt prompt helper. Data powered by [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts).

> The ChatGPT model is a large language model trained by OpenAI that is capable of generating human-like text. By providing it with a prompt, it can generate responses that continue the conversation or expand on the given prompt.

## Feature

![Icon](./images/feature.png)

- [x] Prompts
- [x] Screenshot
- [ ] collection
- [ ] Cloud storage

## Getting Started

First, run the development server:

```bash
pnpm dev
# or
npm run dev
```

Open your browser and load the appropriate development build. For example, if you are developing for the chrome browser, using manifest v3, use: `build/chrome-mv3-dev`.

You can start editing the popup by modifying `popup.tsx`. It should auto-update as you make changes. To add an options page, simply add a `options.tsx` file to the root of the project, with a react component default exported. Likewise to add a content page, add a `content.ts` file to the root of the project, importing some module and do some logic, then reload the extension on your browser.

For further guidance, [visit our Documentation](https://docs.plasmo.com/)

## Making production build

Run the following:

```bash
pnpm build
# or
npm run build
```

This should create a production bundle for your extension, ready to be zipped and published to the stores.

## Submit to the webstores

The easiest way to deploy your Plasmo extension is to use the built-in [bpp](https://bpp.**browser**.market) GitHub action. Prior to using this action however, make sure to build your extension and upload the first version to the store to establish the basic credentials. Then, simply follow [this setup instruction](https://docs.plasmo.com/framework/workflows/submit) and you should be on your way for automated submission!
