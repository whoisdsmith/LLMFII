---
aliases:
  - gpt-project-insight
tags:
  - "#gpt"
  - "#openai"
  - "#api"
  - "#software-development"
  - "#developer-tools"

  - "#electron-app"
  - "#cli-tool"
  - "#project-setup"
---
# GPT Project Insight
* [Project setup](#project-setup)
* [Run Electron app](#run-electron-app)
* [Generate using CLI](#generate-using-cli)
* [Config and Settings](#config-and-options)
* [Examples](#examples)

An engine for generating recursive documentation and using it to work on a project with ChatGPT. To use this application, you need to have an API Key for the [Open AI API](https://platform.openai.com/)

## How it works

### Documentation
<img src="https://i.ibb.co/Vxt6v4g/68747470733a2f2f646f776e6c6f616465722e6469736b2e79616e6465782e72752f707265766965772f3232393838316162.webp" width="440">

### Insight
<img src="https://i.ibb.co/6Yfn6Mb/2023-04-26-21-42-05.png" width="440">

## Project setup
```
npm install
```

## Run Electron app
```
npm run electron:serve
```
### Open By deeplink

```
gptpi://index?dir=C:/path/to/project&config=C:/path/to/config.json&result=C:/path/to/result.json&prompt=PROMPT
```

<img src="https://i.ibb.co/Lr54gDg/localhost-8088-5.png" width="500">

## Generate using CLI

### npx

```
npx tsx .\engine\cli.ts YOUR_API_KEY C:/directory/
```

### help
```
npx tsx .\engine\cli.ts --help
```

### Build the engine and run

```
tsc ./engine/cli.ts --outDir ./out_engine
```
```
node .\out_engine\engine\cli.js YOUR_API_KEY C:/directory/
```

### help
```
node .\out_engine\engine\cli.js --help
```

## Config and options
### Config:
You can load config from CLI using --config option

Config loads automatically from file "SELECTED_DIR/docs.ai.config.json" in the electron app
### Options:
*  --maxTokens <maxTokens>          the maximum number of tokens that the model can accept
*  --bytesPerToken <bytesPerToken>  approximate number of bytes in 
one token
*  --maxQueries <maxQueries>        Maximum number of requests simultaneously
*  --outFile <outFile>              The file to write the result   
*  --config <config>                The file to read the config from
*  --maxTokensFile <maxTokensFile>  The max tokens values for files  --maxTokensDir <maxTokensDir>    The max tokens values for directories
*  --bytesPerToken <bytesPerToken>  approximate number of bytes in 
one token
*  --temperature <temperature>      The temperature of the model   
*  --excludes <excludes>            The pattern to exclude files. Example: dir1,dir2,file3,*.png
*  --model <model>                  The model to use
*  -h, --help                       display help for command
  
## Examples
### Prompt: 
```
Make the footer sticky
```
### Model: GPT-4
<img src="https://i.ibb.co/X3G0VRb/localhost-8083-2.png" width="500">
  
### Prompt: 
```
How to install the project?
```
### Model: GPT-4
<img src="https://i.ibb.co/K2K7bCK/localhost-8083-3.png" width="500">
  
### Prompt: 
```
How to create a script: npm run build_engine
```
### Model: GPT-3.5
<img src="https://i.ibb.co/sjYgBmf/localhost-8083-4.png" width="500">
  
