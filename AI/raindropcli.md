# Raindropcli
_Unofficial raindrop.io command-line interface_

![](https://img.shields.io/github/issues/itsnexn/raindropcli?style=flat-square)
![](https://img.shields.io/github/license/itsnexn/raindropcli?style=flat-square)
![](https://img.shields.io/github/last-commit/itsnexn/raindropcli?style=flat-square)

[![asciicast](https://asciinema.org/a/PqQJmzZFXAppKGmMGiyp7HqrY.svg)](https://asciinema.org/a/PqQJmzZFXAppKGmMGiyp7HqrY)

The primary goal of this script is to integrate with other scripts.
show and list methods have `-r`,`--raw` and `-s`,`--sep` flags that are
relevant in this objective.

## Installation
**NOTE:** Before you run the program, you must create [configuration](#configuration) file.

you can either install the raindropcli using:
```
$ pip install git+https://github.com/itsnexn/raindropcli.git@master
```
or you can clone it and use it as it is.
```
$ git clone https://github.com/itsnexn/raindropcli.git
$ cd raindropcli
$ pip install -r requirements.txt
$ python3 raindropcli.py
```

## Configuration

Make sure you create a configuration file under `$HOME/.raindropcli.conf`
or `$XDG_CONFIG_HOME/raindropcli.conf` directory.

go to [Settings > Integration](https://app.raindrop.io/settings/integrations).
Click on the "Create new app" you may name it whatever you want but I
recommend "raindropcli". following the creation of your new app, click
on it to generate a new test token which you should include in your
configuration file.

Your configuration file should look something like this:
```
# vim: syntax=toml
token = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
```
you don't actually need the vim command. its just for syntax highlighting
for vim.

## TODO

- [ ] Support for child collections
- [ ] Update existing raindrop
- [ ] Remove raindrops using their id
- [x] Add asciinema to the README
- [ ] Border style customizability
- [ ] Add simple cacheing

## License

The files and scripts in this repository are licensed under the MIT License, which
is a very permissive license allowing you to use, modify, copy, distribute, sell,
give away, etc. the software. In other words, do what you want with it. The only
requirement with the MIT License is that the license and copyright notice must be
provided with the software.

#### [License link](./LICENSE.txt)

> _Written by Itsnexn with <3_
