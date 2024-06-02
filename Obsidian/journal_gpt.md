---
aliases:
  - journal-gpt
tags:
  - "#obsidian"
  - "#chatbot"
  - "#openai"
---
## Demo

https://user-images.githubusercontent.com/72312238/229364024-038462e7-9a6a-4912-a2ed-86399fb43da4.mov


## 🚨 DISCLAIMER

This project is inspired by [Notion Chat Langchain](https://github.com/mayooear/notion-chat-langchain) [Mayo](https://twitter.com/mayowaoshin).

## A ChatBot for Obsidian Notes

This repo uses vector embedding and turns your Obsidian notes into a chatbot.

## Development

1. Clone the repo
2. Install packages

```
pnpm install
```

3. Set up your `.env` file

- Copy `.env.example` into `.env`
  Your `.env` file should look like this:

```
OPENAI_API_KEY=

PINECONE_API_KEY=
PINECONE_ENVIRONMENT=

```

- Visit [openai](https://help.openai.com/en/articles/4936850-where-do-i-find-my-secret-api-key) and [pinecone](https://www.pinecone.io/) to retrieve API keys and insert into your `.env` file.

4. In the `config` folder, go into `pinecone-index.ts` and replace `PINECONE_INDEX_NAME` with the index name in your pinecone dashboard.

## 🧑 Instructions for ingesting your own dataset

Create an Obsidian_Notes folder in root project and copy and paste your .md Obsidian notes into it.

## Ingest data

Now we need to `ingest` your docs. In **very** simple terms, ingesting is the process of converting your docs into numbers (embedding) that can be easily stored and analyzed for similarity searches.

```bash
npm run ingest

```

## Running the app

Run your local dev environment `npm run dev`.

Use the search bar to ask a question about your docs.

Simple.

## Deployment

You can deploy this app to the cloud with [Vercel](https://vercel.com) ([Documentation](https://nextjs.org/docs/deployment)).

## Credit

This repo is inspired by [Notion Chat Langchain](https://github.com/mayooear/notion-chat-langchain) and [notion-qa](https://github.com/hwchase17/notion-qa).
