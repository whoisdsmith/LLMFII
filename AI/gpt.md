---
aliases:
  - GPT
tags:
  - "#software-development"
  - "#developer-tools"
  - "#open-source"

  - "#jekyll-theme"
  - "#github-pages"
  - "#infosec"
---
# The Hacker Plus theme

Hacker Plus is a Jekyll theme for GitHub Pages based on [The Hacker Theme](https://pages-themes.github.io/hacker) with added cool new features optimised for those who like to spread their knowledge in the InfoSec or Competitive Programming fields by writing writups/solutions for the problems they have solved during a CTF or Programming Contest

*Run the script -> Write in markdown -> Push commit -> The site is generated automatically*

*You can [preview the theme to see what it looks like](https://CaptainIRS.github.io/hacker-plus-theme), or even [use it today](#usage).*
*You can also visit my [personal site](https://CaptainIRS.github.io) to see the theme used in an actual website*

*The theme is optimised for easy use in VS Code with some useful snippets to reduce the burden*

## Added Features

* UI improvements with mobile compatibility
* Scripts for automatic generation of boilerplate templates for each writeup/solution
* Social media links
* Disqus comments section
* Easy google site verification, google analytics integration
* Post share buttons(for Facebook, Twitter and LinkedIn)
* Automatic sitemap generation for improved SEO
* Search by tag functionality
* Anchors for subheadings
* Code markdown using Prism.js instead of rogue
  * Line number support
  * Code copy and download support
  * Syntax highlighting for numerous languages
  * Support for font ligatures in code like that for `=>`, `!=`, etc.
* Optimisations for CTF Writeups:
  * Automatically generate the top level writeups.html page with proper categorisation
  * Automatically add side nav bar to show other writeups in the same CTF
  * Automatically generate beautiful headers for each writeup
* Optimisations for CP Solutions:
  * Automatically fetch and render problem statements from platforms like Codechef
  * Automatically generate the top level solutions.html page with proper categorisation
  * Automatically add side nav bar to show other solutions in the same contest
  * Automatically generate beautiful headers for each solution

*Some useful snippets for markdown included in the template project:*

| Prefix       | Description                                        |
|:-------------|:---------------------------------------------------|
| cmdbashdown  | To add a code block with bash prompt and download  |
| cmdbash      | To add a code block with bash prompt               |
| cmdotherdown | To add a code block with other prompt and download |
| cmdother     | To add a code block with other prompt              |
| down         | Downloadable code                                  |
| linenum      | Code block with line numbers                       |
| linenumdown  | Downloadable code with line numbers                |

## Usage

To use the Hacker Plus theme:

*(Assuming that you have VS Code and python already installed)*

1. Go to [CaptainIRS/hacker-plus-template](https://github.com/CaptainIRS/hacker-plus-template) and click on 'Use this template'. Then fill in the asked details. This repo contains the basic structure, useful snippets for markdown in VS Code and a Gemfile in case you want to build and test the site locally
2. Enable GitHub Pages in your repository
3. Clone the repo locally and run `git submodule add https://github.com/CaptainIRS/hacker-plus-scripts scripts` to get the required python scripts
4. Fill in in the desired fields the `_config.yml` file and push the commits to have a working site
5. To get started, follow the instructions below(in VS Code):

Writing CTF Writeups:

1. Open a new terminal window in VS Code and run `cd scripts`
2. Run `python writeup_gen.py` and fill in the details. The script would generate the required writeup files and asset directory for the CTF and open the required files in VS Code for editing
3. Write the writeups in markdown and push the commits to your repo

Writing Codechef Problem Solutions:

1. Open a new terminal window in VS Code and run `cd scripts`
2. Run `python codechef_gen.py` and fill in the details. The script would generate the required solution files and open them in VS Code for editing
3. Write the solutions in markdown and push the commits to your repo

## Customizing

### Stylesheet

If you'd like to add your own custom styles:

1. Create a file called `/assets/css/style.scss` in your site
2. Add the following content to the top of the file, exactly as shown:
    ```scss
    ---
    ---

    @import "{{ site.theme }}";
    ```
3. Add any custom CSS (or Sass, including imports) you'd like immediately after the `@import` line

## Roadmap

See the [open issues](https://github.com/CaptainIRS/hacker-plus-theme/issues) for a list of proposed features (and known issues).

## Upcoming features

 - [ ] Support for more CP platforms(Codeforces, TopCoder, etc.)

## Contributing

Contributions are welcome! If you'd like a feature to be added, submit an issue or make a pull request

### Previewing the theme locally

If you'd like to preview the theme locally (for example, in the process of proposing a change):

1. Clone down the theme's repository (`git clone https://github.com/CaptainIRS/hacker-plus-theme`)
2. `cd` into the theme's directory
3. Run `gem install bundler` and `bundle install` to install the necessary dependencies
4. Run `bundle exec jekyll serve` to start the preview server
5. Visit [`localhost:4000`](http://localhost:4000) in your browser to preview the theme

## License

The theme is licensed under MIT License
