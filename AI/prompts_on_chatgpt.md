---
aliases:
  - prompts-on-chatgpt
tags:
  - awesome-list
  - chatgpt
  - github
  - "#chatgpt"
  - "#openai"
  - "#chatgpt-alternative"
  - "#developer-tools"
  - "#open-source"

  - "#userscript"
  - "#automation"
  - "#customization"
---
# prompts-on-chatgpt

![](https://github.com/dsymbol/prompts-on-chatgpt/assets/88138099/0e0972da-d046-408e-b728-16ad68acbbd8)

UserScript that adds [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) commands to ChatGPT.

## Installation

Install a userscript manager such as [Violentmonkey](https://github.com/Violentmonkey/Violentmonkey) or [Tampermonkey](https://github.com/Tampermonkey/tampermonkey), then click [here](https://raw.githubusercontent.com/dsymbol/prompts-on-chatgpt/main/poc.user.js) to install the script.

## Usage

1. Open a [ChatGPT](https://chat.openai.com/chat) chat.
2. Type the command prefix (/) in the message text area.
3. A list of available commands will appear, which can be navigated using the up and down arrow keys, and selected by clicking on the command.
4. The selected command's value will be inserted into the message text area.

## Customization

The [default](https://github.com/dsymbol/prompts-on-chatgpt/blob/main/prompts.json) list of commands and their corresponding autocomplete values can be overridden by passing your own raw JSON file URL in the script headers.

```js
// @resource data https://raw.githubusercontent.com/username/repository/branch/prompts.json
```

This will replace the default `prompts.json` file with the one from the specified URL, Please make sure that the JSON file is formatted correctly and accessible to the script.

## Credits

- [f/awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts)
- [lencx/ChatGPT](https://github.com/lencx/ChatGPT)
