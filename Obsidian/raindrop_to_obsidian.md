# raindrop-to-obsidian
This is a little python script that helps me writing a weekly review blogpost of what happened the last week.
over the week I collect blogposts in [Raindrop.IO](https://raindrop.io/), this script grabs all the saved blogposts from one specified collection and exports it to a markdown file, sorted by tags, in my [Obsidian](https://obsidian.md/) vault.
This script is only tested on a MAC!

## Requirements
This project is dependend on [https://github.com/atsuoishimoto/python-raindropio](https://github.com/atsuoishimoto/python-raindropio) so install it first.

## Usage
It makes use of the [Raindrop.IO API](https://developer.raindrop.io/), so first you need to [register an app](https://app.raindrop.io/settings/integrations) and obtain an Raindrop.IO API Key.
Enter this API Key in script.

To get the ID of your blog collection, simply copy the number from the url when you open the raindrop collection in your browser.
e.g. ```https://app.raindrop.io/my/123456```
Enter this collection ID in the script.

Enter the full path to the folder in your obsidian vault where the blog posts should be stored.
For example here on my mac that would be something like "/Users/demouser/documents/obsidian/Blog/"

Enter your obsidian vault name in the script.

Run it with
```bash
python3 raindrop-to-obsodian.py
```

## ToDo
- [ ] Error handling 😉
