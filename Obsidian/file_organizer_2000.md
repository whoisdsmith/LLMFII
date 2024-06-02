---
tags:
  - "#ai"
  - "#openai"
  - "#llm"
  - "#open-source"
  - "#developer-tools"

  - "#file-organization"
  - "#obsidian-plugin"
  - "#self-hosting"
---
We ship daily - try to keep F02k version up to date

<a href="https://discord.gg/udQnCRFyus"><img src="https://raw.githubusercontent.com/unslothai/unsloth/main/images/Discord button.png" height="48"></a>

# AI File Organizer 2000

This is an Obsidian Plugin that uses AI to help you keep your files organized. It tags, renames, and moves files to the most appropriate folders in your vault. You'll also be able to transcribe audios, to have your images annotated, and to create AI templates.

### Features

- Automatically move files to the correct folder
- AI suggestions to organize your files. Apply tags, aliases, rename & more
- Supports text, audio, and images
- Create and apply custom AI templates
- Local-first LLM support (see advanced settings in plugin)

  <img width="900" alt="Screenshot 2024-04-30 at 14 05 30" src="https://github.com/different-ai/file-organizer-2000/assets/11430621/2e2cdf14-c6d0-4fd0-8e02-268928ad7ef3">

## Tips and Tricks

[![Thumbnail (2)](https://github.com/different-ai/file-organizer-2000/assets/11430621/1b2c524b-11bc-484d-9255-4699783303bf)](https://youtube.com/playlist?list=PLgRcC-DFR5jdUxbSBuNeymwYTH_FSVxio&si=I7VpzzAnY0XVQ15c)

## How to use

### A. Get suggestions and choose what to apply with AI Assistant View 

1. Click on the Assistant View Icon or set up the "Show Assistant" hotkey to open the Sidebar
2. Select any of your files and choose which changes to apply

<img width="1277" alt="Screenshot 2024-05-24 at 11 42 17 PM" src="https://github.com/different-ai/file-organizer-2000/assets/46509400/dc06a61f-64d0-4e10-898d-3e0330004e94">

### B. or Auto-Organize with the AI Inbox

We recommend the AI Assistant view for more control. But the AI Inbox can be handy as well. Simply move any of your files to the "Inbox" folder and the plugin will automatically move it to the folder it belongs. Additional configuration can also be specified within the plugin settings.

Place your unorganized files into `_FileOrganizer2000/Inbox`

![image](https://github.com/different-ai/file-organizer-2000/assets/11430621/295038f0-170c-456e-8e0a-e89c31719b95)

It takes a sec, and then renames, and organizes your file.

![image](https://github.com/different-ai/file-organizer-2000/assets/11430621/f9fd716f-6ada-45c4-bd59-a4efcd79b0e5)

See plugin settings to customize the changes AI Inbox applies to your files.


### C. Create custom AI Templates

See video: https://www.youtube.com/watch?v=rommuUXRgUw&t=17s


## Setup

Choose between any of the three setups below

### A. Pro Access

1. Go to general settings inside the plugin settings
2. Choose "Use Pro Account"
3. Click login and follow instructions

### B. Use your own LLM (without self-hosting)

1. Go to general settings inside the plugin settings
2. Get your OpenAI API key + top up with credits
3. Paste the API key in the OpenAI API Key input
4. That's it you should be ready to go!

<img width="836" alt="byok" src="https://github.com/different-ai/file-organizer-2000/assets/46509400/2bcc6824-236d-40ae-895b-d501401238bd">



### C. Self-hosting

1. Run the server

   For Linux/macOS:

   ```sh
   cd ./app
   npm i && npm run build
   OPENAI_API_KEY=[your open ai api key] npm run start
   ```

   Replace `[your open ai api key]` with your actual OpenAI API key.

   For Windows (PowerShell):

   ```sh
   cd .\app
   npm i; npm run build
   $env:OPENAI_API_KEY="your open ai api key"; npm run start
   ```

   Replace `your open ai api key` with your actual OpenAI API key.

2. Go inside the Settings of the plugin and enable "Self-hosted"

<img width="707" alt="Screenshot 2024-04-13 at 07 16 21" src="https://github.com/different-ai/file-organizer-2000/assets/11430621/ca2222c9-cb8d-4d15-8459-2da4c9662f24">

## Community

Join the [discord server](https://discord.gg/udQnCRFyus) for more.

## Small iOS shortcut for easy access

The iOS shortcut below makes it easy for you to easily work from your phone with this plugin.

https://www.icloud.com/shortcuts/06915768862848fb9711f2f19b6405e2

## To Do

- [ ] Replace GPT Vision by a local model
- [ ] Make it easy for people to extend whatever workflow.

### Notes

This plugin interacts with your filesystem.
