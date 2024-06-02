---
aliases:
  - Vontigo
tags:
  - opensource
  - ai
  - sveltekit
  - "#open-source"
  - "#ai"
  - "#sveltekit"
  - "#cms"
  - "#chatgpt"

  - "#content-management-system"
  - "#automated-content-creation"
  - "#full-stack-framework"
---
### Revolutionize Content Creation with Vontigo

# The AI-Powered, Full-Stack CMS & Mobile App Built with SvelteKit

[![Node.js CI](https://github.com/Vontigo/Vontigo/actions/workflows/node.js.yaml/badge.svg)](https://github.com/Vontigo/Vontigo/actions/workflows/node.js.yaml)

![feature-image](https://github.com/Vontigo/Vontigo/assets/3785721/04228bea-f654-44a1-ba16-fa3b22706ba7)

Vontigo is a cutting-edge open-source Content Management System (CMS) that leverages the power of SvelteKit to deliver fast, responsive, and dynamic websites. With its integrated ChatGPT feature, Vontigo takes content creation to the next level by generating high-quality articles automatically, saving time and effort for both developers and content creators.

Vontigo's full-stack SvelteKit architecture enables seamless server-side rendering and client-side routing, allowing for lightning-fast page loads and smooth user experiences. The CMS also includes a range of built-in features, such as customizable themes, page templates, and an intuitive admin dashboard, making it easy for users to create, manage and publish content.

Investors and developers alike will appreciate Vontigo's innovative use of AI technology to automate content creation, streamlining workflows and reducing costs. With its user-friendly interface, flexible customization options, and advanced features, Vontigo is a powerful and adaptable CMS that can meet the needs of any business or organization.

- Saves time and effort with automatic content generation, freeing up resources for other tasks.
- Utilizes cutting-edge AI technology to deliver high-quality, relevant content at scale.
- Built on SvelteKit, a modern full-stack framework that allows for fast and responsive websites.
- Offers a range of built-in features and customization options to meet the needs of different users and use cases.
- Open-source codebase allows for flexibility, customization, and community contributions.

At Vontigo, we're passionate about building a world-class CMS that empowers users to create and manage content with ease. Our platform draws inspiration from a range of cutting-edge technologies, including [BrainiacMinds](https://brainiacminds.com/) (powered by [ChatGPT](https://openai.com/)), [SvelteKit](https://kit.svelte.dev/), [Capacitor](https://capacitorjs.com/), [Mixcore CMS](https://mixcore.org/), and [Ghost](https://ghost.org/).

With Vontigo, you'll enjoy a range of powerful features, including automated content creation, personalized content delivery, predictive analytics, improved search capabilities, chatbots, and social media management.

Our open-source platform is cost-effective, easy to use, and endlessly customizable, making it the ideal solution for businesses of all sizes. Whether you're looking to streamline your content strategy, boost engagement, or drive revenue growth, Vontigo has everything you need to succeed. Try it out today and see the difference for yourself!

We warmly invite you to discover the exciting world of Vontigo with us and kindly ask for your support by visiting our Product Hunt page at <https://www.producthunt.com/posts/vontigo> and giving us an upvote - together, let's make Vontigo soar!

<a href="https://www.producthunt.com/posts/vontigo?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-vontigo" target="_blank"><img src="https://api.producthunt.com/widgets/embed-image/v1/featured.svg?post_id=394092&theme=light" alt="Vontigo - 🤖&#0032;The&#0032;AI&#0045;Powered&#0044;&#0032;Full&#0045;Stack&#0032;CMS&#0032;Built&#0032;with&#0032;SvelteKit | Product Hunt" style="width: 250px; height: 54px;" width="250" height="54" /></a>

## Tech stacks & Services

<picture>
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Svelte_Logo.svg/640px-Svelte_Logo.svg.png" alt="sveltekit" height="50px"/></picture>
<picture>
  <img src="https://upload.wikimedia.org/wikipedia/commons/d/d5/Tailwind_CSS_Logo.svg" alt="tailwindcss" height="50px"/>
</picture>
<picture>
 <img alt="skeletonui" src="https://github.com/skeletonlabs/skeleton/blob/f6ae5ae2e96940b6c53dec84fc358835a373194f/static/favicon.png" height="50px">
</picture>
<picture>
 <img alt="capacitorjs" src="https://ionic.io/_next/image?url=%2F_next%2Fstatic%2Fmedia%2Flogo-capacitor.aa4b0dd5.png&w=64&q=75" height="50px">
</picture>
<picture>
 <img alt="turbo" src="https://turbo.build/images/docs/repo/repo-hero-logo-dark.svg" height="50px">
</picture>

<picture>
  <img src="https://seeklogo.com/images/O/open-ai-logo-8B9BFEDC26-seeklogo.com.png" alt="openai" height="50px"/>
</picture>
<picture>
  <img alt="AuthJS" src="https://authjs.dev/img/logo/logo-sm.webp" height="50px">
</picture>
<picture>
  <img alt="BrainiacMinds.com" src="https://play-lh.googleusercontent.com/2hKdiuS26NkQCdwz6QX46EyLKEfw65PTuDt_yGMaOsDpEImZFH2-JoQLqT89KBorfEs=w480-h960-rw" height="50px">
</picture>

## Quickstart install

### 1. Create GitHub fork

First you’ll need to make a fork of the Vontigo repository. Click on the fork button right at the top, wait for a copy to be created over on your personal GitHub account, and you should be all set!

### 2. Configure repository

The main Ghost repository is a monorepo that using Turborepo containing the full Ghost code, including the Admin client and default theme which will also be automatically set up.

```bash
# First clone Ghost with submodules and make it your working dir
git clone --recurse-submodules git@github.com:Vontigo/Vontigo && cd Vontigo
```

### 3. Properly rename your references

```bash
# Rename origin to upstream
git remote rename origin upstream

# Add your fork as an origin, editing in <YourUsername>!
git remote add origin git@github.com:<YourUsername>/Vontigo.git
```

### 4. Run setup & installation

> ⚠️ Rename `.env.example` to `.env`.

#### 4.1 Run with [Turborepo](https://turbo.build/repo/docs/installing)

Turbo is an incremental bundler and build system optimized for JavaScript and TypeScript, written in Rust.

```bash
# Only ever run this once
pnpm install turbo --global

# Only ever run this once
pnpm i

# Run Vontigo in development mode
pnpm dev

# web:dev:      ➜  Local:   https://localhost:5173/
# mobile:dev:   ➜  Local:   http://localhost:5174/
# docs:dev:     ➜  Local:   http://localhost:5175/
```

> 🌐 Vontigo website is now running at `https://localhost:5173/` -
> 📱 Vontigo mobile app is now running at `http://localhost:5174/`

#### 4.2 Or, run as SvelteKit app

```bash
cd .\apps\web\
pnpm i
pnpm run dev -- --open
```

> ⚠️ Incase you are not able to see the `Setup` screen. Make sure you have deleted the `./apps/web/database/vontigo.db` file.

## Source Tree

```bash
./apps
├── docs    # Development docs
├── mobile  # Mobile App using SvelteKit & Capacitor
└── web     # Website & API using SvelteKit
```

## Contribution

Please make sure to read the [Contributing Guide](https://github.com/Vontigo/Vontigo/blob/main/CODE_OF_CONDUCT.md) before making a pull request. If you have a Vontigo-related project/component/tool, add it with a pull request to [this curated list](https://github.com/vontigo/awesome-vontigo)!

Thank you to all the people who already contributed to Vontigo!

<a href="https://github.com/vontigo/vontigo/graphs/contributors"><img src="https://opencollective.com/vontigo/contributors.svg?width=890" /></a>

## Repo analytics

![Alt](https://repobeats.axiom.co/api/embed/3b17802e07552dafda67897334dfa36a15af04f2.svg 'Repobeats analytics image')

## Copyright & license

Copyright (c) 2023-2023 Vontigo Foundation - Released under the MIT license. Vontigo and the Vontigo Logo are trademarks of Vontigo Foundation Ltd. Please see our trademark policy for info on acceptable usage.
