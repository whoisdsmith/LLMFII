---
aliases: [howdoi, howdoi_1717218874711]
tags: [open-source, cli-tool, developer-tools, "#command-line", "#developer-tools", "#cli", "#python", "#documentation", "|", "#coding-answers", "#instant-help", "#howdoi"]
---

# Howdoi

## Description

Instant coding answers via the command line

## README

<p align="center">
    <a href="https://pypi.python.org/pypi/howdoi">
        <img src="https://www.dropbox.com/s/dk13iy2uoufdwr7/HowDoIcolor512.png?raw=1" alt="Sherlock, your neighborhood command-line sloth sleuth" />
    </a>
</p>
<h1 align="center">howdoi</h1>
<h2 align="center">Instant coding answers via the command line</h2>
<p align="center"><strong>⚡ Never open your browser to look for help again ⚡</strong></p>

<p align="center">
    <a href="https://github.com/gleitz/howdoi/actions?query=workflow%3A%22Python+CI%22"><img src="https://img.shields.io/github/workflow/status/gleitz/howdoi/Python%20CI?style=plastic&color=78dce8" alt="build status"></a>
    <a href="https://pepy.tech/project/howdoi"><img src="https://img.shields.io/badge/dynamic/json?style=plastic&color=ab9df2&maxAge=86400&label=downloads&query=%24.total_downloads&url=https%3A%2F%2Fapi.pepy.tech%2Fapi%2Fprojects%2Fhowdoi" alt="downloads"></a>
    <a href="https://pypi.python.org/pypi/howdoi"><img src="https://img.shields.io/pypi/pyversions/howdoi.svg?style=plastic&color=ff6188" alt="Python versions"></a>
</p>

------------------------------------------------------------------------

## Introduction to Howdoi

Are you a hack programmer? Do you find yourself constantly Googling for
how to do basic programming tasks?

Suppose you want to know how to format a date in bash. Why open your
browser and read through blogs (risking major distraction) when you can
simply stay in the console and ask howdoi:

    $ howdoi format date bash
    > DATE=`date +%Y-%m-%d`

howdoi will answer all sorts of queries:

    $ howdoi print stack trace python
    > import traceback
    >
    > try:
    >     1/0
    > except:
    >     print '>>> traceback <<<'
    >     traceback.print_exc()
    >     print '>>> end of traceback <<<'
    > traceback.print_exc()

    $ howdoi convert mp4 to animated gif
    > video=/path/to/video.avi
    > outdir=/path/to/output.gif
    > mplayer "$video" \
    >         -ao null \
    >         -ss "00:01:00" \  # starting point
    >         -endpos 10 \ # duration in second
    >         -vo gif89a:fps=13:output=$outdir \
    >         -vf scale=240:180

    $ howdoi create tar archive
    > tar -cf backup.tar --exclude "www/subf3" www

[![image](http://imgs.xkcd.com/comics/tar.png)](https://xkcd.com/1168/)

## Installation

    pip install howdoi

## Usage

### New to Howdoi?

    howdoi howdoi

### RTFM

- [Introduction and
    installation](http://gleitz.github.io/howdoi/introduction/)
- [Usage](http://gleitz.github.io/howdoi/usage/)
- [Contributing to
    howdoi](http://gleitz.github.io/howdoi/contributing_to_howdoi/)
- [Advanced
    usage](http://gleitz.github.io/howdoi/howdoi_advanced_usage/)
- [Troubleshooting](http://gleitz.github.io/howdoi/troubleshooting/)

### Commands

    usage: howdoi [-h] [-p POS] [-n NUM] [-a] [-l] [-c] [-x] [-C] [-j] [-v] [-e [ENGINE]]
    [--save] [--view] [--remove] [--empty] [QUERY ...]

    instant coding answers via the command line

    positional arguments:
      QUERY                 the question to answer

    optional arguments:
      -h, --help            show this help message and exit
      -p POS, --pos POS     select answer in specified position (default: 1)
      -n NUM, --num NUM     number of answers to return (default: 1)
      -a, --all             display the full text of the answer
      -l, --link            display only the answer link
      -c, --color           enable colorized output
      -x, --explain         explain how answer was chosen
      -C, --clear-cache     clear the cache
      -j, --json            return answers in raw json format
      -v, --version         display the current version of howdoi
      -e [ENGINE], --engine [ENGINE]
                            search engine for this query (google, bing, duckduckgo)
      --save, --stash       stash a howdoi answer
      --view                view your stash
      --remove              remove an entry in your stash
      --empty               empty your stash

    environment variable examples:
      HOWDOI_COLORIZE=1
      HOWDOI_DISABLE_CACHE=1
      HOWDOI_DISABLE_SSL=1
      HOWDOI_SEARCH_ENGINE=google
      HOWDOI_URL=serverfault.com

Using the howdoi stashing feature (for more advanced features view the
[keep documentation](https://github.com/OrkoHunter/keep)).

    stashing: howdoi --save QUERY
    viewing:  howdoi --view
    removing: howdoi --remove (will be prompted which answer to delete)
    emptying: howdoi --empty (empties entire stash, will be prompted to confirm)

As a shortcut, if you commonly use the same parameters each time and
don\'t want to type them, add something similar to your .bash_profile
(or otherwise). This example gives you 5 colored results each time.

    alias h='function hdi(){ howdoi $* -c -n 5; }; hdi'

And then to run it from the command line simply type:

    $ h format date bash

You can also search other [StackExchange
properties](https://stackexchange.com/sites#traffic) for answers:

    HOWDOI_URL=cooking.stackexchange.com howdoi make pesto

or as an alias:

    alias hcook='function hcook(){ HOWDOI_URL=cooking.stackexchange.com howdoi $* ; }; hcook'
    hcook make pesto

Other useful aliases:

    alias hless='function hdi(){ howdoi $* -c | less --raw-control-chars --quit-if-one-screen --no-init; }; hdi'

## Contributors

- Benjamin Gleitzman ([\@gleitz](http://twitter.com/gleitz))
- Yanlam Ko ([\@YKo20010](https://github.com/YKo20010))
- Diana Arreola ([\@diarreola](https://github.com/diarreola))
- Eyitayo Ogunbiyi ([\@tayoogunbiyi](https://github.com/tayoogunbiyi))
- Chris Nguyen ([\@chrisngyn](https://github.com/chrisngyn))
- Shageldi Ovezov ([\@ovezovs](https://github.com/chrisngyn))
- Mwiza Simbeye
    ([\@mwizasimbeye11](https://github.com/mwizasimbeye11))
- Shantanu Verma ([\@SaurusXI](https://github.com/SaurusXI))
- Sheza Munir ([\@ShezaMunir](https://github.com/ShezaMunir))
- Jyoti Bisht ([\@joeyouss](https://github.com/joeyouss))
- And [more!](https://github.com/gleitz/howdoi/graphs/contributors)

## How to Contribute

We welcome contributions that make howdoi better and improve the
existing functionalities of the project. We have created a separate
[guide to contributing to
howdoi](http://gleitz.github.io/howdoi/contributing_to_howdoi/) that explains
how to get up and running with your first pull request.

## Notes

- Works with Python 3.5 and newer. Unfortunately Python 2.7 support
    has been discontinued :(
- There is a [GUI that wraps
    howdoi](https://pypi.org/project/pysimplegui-howdoi/)
- There is a [Flask webapp that wraps
    howdoi](https://howdoi.maxbridgland.com)
- An [Alfred Workflow](http://blog.gleitzman.com/post/48539944559/howdoi-alfred-even-more-instant-answers)
    for howdoi
- Slack integration available through
    [slack-howdoi](https://github.com/ellisonleao/slack-howdoi)
- Telegram integration available through
    [howdoi-telegram](https://github.com/aahnik/howdoi-telegram)
- Special thanks to Rich Jones
    ([\@miserlou](https://github.com/miserlou)) for the idea
- More thanks to [Ben Bronstein](https://benbronstein.com/) for the
    logo

## Visual Studio Code Extension Installation

Head over to the [MarketPlace](https://marketplace.visualstudio.com/items?itemName=howdoi-org.howdoi)
to install the extension.

# News

2.0.20
------
- Update dependency versions
- Add support for Python 3.10

2.0.19
------
- Fix typo

2.0.18
------
- Fixed issue with howdoi cache where cache misses would be printed to the console

2.0.17
------
- New documentation and mkdocs
- Fixed issue with how howdoi chooses the proper search engine (command line flags now override environment variables)
- Added a search engine fallback if one of the search engines fails
- Fixed issue with howdoi cache

2.0.16
------
- Fix GDPR issue for those using howdoi in countries outside the US
- Better support for using `HOWDOI_URL`

2.0.15
------
- Add explainability with `-x` or `--explain` options
- Better error checking for when search engines block queries
- Using improved DuckDuckGo endpoint
- Answer pages now fetched in parallel for speed improvement

2.0.14
------
- Fix a number of bugs by switching from parsing Google links to looking for URLs instead

2.0.13
------
- More permanent fix for extracting Google links

2.0.12
------
- Hotfix for Google link formatting

2.0.11
------
- Hotfix for Google link formatting

2.0.10
------
- Hotfix for new Google classnames
- Separate requirements.txt files for prod and dev

2.0.9
------
- Cleaner command line options that also include environment variables
- README updates

2.0.8
------
- Fix issue for answers that have no code in the answer but code in the comments
- Add range checks for -n and -p flags
- Moved from Travis to Github Actions
- Dropped Python 2.7 support

2.0.7
------
- Update for new Google CSS style

2.0.6
------
- Fix issue where `-a` would not return a proper response due to updated CSS on StackOverflow

2.0.5
------
- New logo and colors!

2.0.4
------
- Cachelib rollback to support Python 2.7
- Better error message when Google is being blocked (for example in China)

2.0.3
------
- Bring back Python 2.7 support (for now)

2.0.2
------
- Fixed keep support for stashing and viewing answers

2.0.1
------
- Added JSON output with the -j flag (great for consuming howdoi results for use in other apps)
- Added stashing ability for saving useful answer for later (based on https://github.com/OrkoHunter/keep)
- Added caching for tests to prevent being rate limited by Google while developing
- Added easier method for calling howdoi when imported (howdoi.howdoi)

1.2.1
------
- Fix dependency issue

1.2.0
------
- Massive speed improvements of startup, answer fetching, and caching
- Command line flags for alternate search engines
- Remove duplicate answers

1.1.14
------
- Links displayed with markdown syntax
- Improved performance and caching (again)

1.1.13
------
- Improved performance and caching
- More friendly answer display
- Added support for Python 3.6
- Removed support for Python 2.6

1.1.12
------
- Add additional search engine support

1.1.11
------
- Fix issue with UTF-8 encoding

1.1.10
------
- Include the link in output when asking for >1 answer
- Compatibility with linuxbrew

1.1.9
------
- Fix issue with upload to PyPI

1.1.8
------
- Fix colorization when HOWDOI_COLORIZE env variable is enabled
- Fix certificate validation when SSL disabled

1.1.7
------
- Add Localization support with HOWDOI_LOCALIZATION env variable (Currently only pt-br and en)

1.1.6
------
- Updates for Python3
- Updates for caching

1.1.5
------
- Updates for Python3
- Fix issues with cache
- Allow disabling SSL when accessing Google

1.1.4
------
- Added caching

1.1.3
------
- Added fix to handle change in Google search page HTML
- Updated Travis CI tests

1.1.2
------
- Compatibility fixes for Python3.2
- Travis CI tests now being run for Python 2.6, 2.7, 3.2, and 3.3

1.1.1
------
- Added message when question has no answer

1.1
------
- Added multiple answers with -n/--num-answers flag
- Added colorized output with -c/--color flag
- Added answer link to the bottom of questions with -a/--all flag
- Unit tests now managed through Travis CI

1.0
------
- Added support for Python3
- Switched to the requests library instead of urllib2
- Project status changed to Production/Stable
- Added troubleshooting steps to the README

0.2
------
- Added sane flags
- Now using ``/usr/bin/env python`` instead of ``/usr/bin/python``
- Updated README for brew installation instructions

0.1.2
------
- Added Windows executable
- Updated README for pip installation instructions

0.1.1
------
- Added to PyPI

0.1
------
- We're doing it live!
