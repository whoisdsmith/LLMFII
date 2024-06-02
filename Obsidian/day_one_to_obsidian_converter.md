---
aliases:
  - day-one-to-obsidian-converter
tags:
  - markdown
  - obsidian
  - converter
  - "#software-development"
  - "#open-source"
  - "#document-parsing"

  - "#php"
  - "#obsidian"
  - "#dayone"
---
# day-one-to-obsidian-converter

[![Integrate](https://github.com/ergebnis/day-one-to-obsidian-converter/workflows/Integrate/badge.svg)](https://github.com/ergebnis/day-one-to-obsidian-converter/actions)
[![Merge](https://github.com/ergebnis/day-one-to-obsidian-converter/workflows/Merge/badge.svg)](https://github.com/ergebnis/day-one-to-obsidian-converter/actions)
[![Release](https://github.com/ergebnis/day-one-to-obsidian-converter/workflows/Release/badge.svg)](https://github.com/ergebnis/day-one-to-obsidian-converter/actions)
[![Renew](https://github.com/ergebnis/day-one-to-obsidian-converter/workflows/Renew/badge.svg)](https://github.com/ergebnis/day-one-to-obsidian-converter/actions)

[![Code Coverage](https://codecov.io/gh/ergebnis/day-one-to-obsidian-converter/branch/main/graph/badge.svg)](https://codecov.io/gh/ergebnis/day-one-to-obsidian-converter)
[![Type Coverage](https://shepherd.dev/github/ergebnis/day-one-to-obsidian-converter/coverage.svg)](https://shepherd.dev/github/ergebnis/day-one-to-obsidian-converter)

[![Latest Stable Version](https://poser.pugx.org/ergebnis/day-one-to-obsidian-converter/v/stable)](https://packagist.org/packages/ergebnis/day-one-to-obsidian-converter)
[![Total Downloads](https://poser.pugx.org/ergebnis/day-one-to-obsidian-converter/downloads)](https://packagist.org/packages/ergebnis/day-one-to-obsidian-converter)
[![Monthly Downloads](http://poser.pugx.org/ergebnis/day-one-to-obsidian-converter/d/monthly)](https://packagist.org/packages/ergebnis/day-one-to-obsidian-converter)

This project provides a [`composer`](https://getcomposer.org) package with  a console command for converting [DayOne](https://dayoneapp.com) journals to [Obsidian](https://obsidian.md) notes.

## Installation

Run

```sh
composer require ergebnis/day-one-to-obsidian-converter
```

## Usage

Run

```sh
php bin/day-one-to-obsidian-converter <day-one-directory> <obsidian-vault-directory>
```

The command will

- look for JSON files in `<day-one-directory>`
- convert JSON files that  match the JSON Schema in [`resource/day-one/schema.json`](resource/day-one/schema.json) to Markdown files in `<obsidian-vault-directory>`

Ideally, the `<obsidian-vault-directory>` should not exist yet.

## Demo

Run

```sh
git clone git@github.com:ergebnis/day-one-to-obsidian-converter.git
```

to clone this repository.

Run

```sh
composer install
```

to install dependencies with `composer`.

Run

```sh
php bin/day-one-to-obsidian-converter demo/day-one demo/obsidian
```

to see the converter in action.

## Changelog

The maintainers of this project record notable changes to this project in a [changelog](CHANGELOG.md).

## Contributing

The maintainers of this project suggest following the [contribution guide](.github/CONTRIBUTING.md).

## Code of Conduct

The maintainers of this project ask contributors to follow the [code of conduct](.github/CODE_OF_CONDUCT.md).

## General Support Policy

The maintainers of this project provide limited support.

You can support the maintenance of this project by [sponsoring @localheinz](https://github.com/sponsors/localheinz) or [requesting an invoice for services related to this project](mailto:am@localheinz.com?subject=ergebnis/day-one-to-obsidian-converter:%20Requesting%20invoice%20for%20services).

## PHP Version Support Policy

This project supports PHP versions with [active and security support](https://www.php.net/supported-versions.php).

The maintainers of this project add support for a PHP version following its initial release and drop support for a PHP version when it has reached the end of security support.

## Security Policy

This project has a [security policy](.github/SECURITY.md).

## License

This project uses the [MIT license](LICENSE.md).

## Credits

This converter is inspired by [`quantumgardener/dayone-to-obsidian`](https://github.com/quantumgardener/dayone-to-obsidian).

The list of non-printable characters for the [`RemoveNonPrintableCharacters`](src/Inside/Domain/DayOneToObsidian/Text/RemoveNonPrintableCharacters.php) text processor is obtained from [`PhpCsFixer\Fixer\Basic\NonPrintableCharacterFixer`](https://github.com/FriendsOfPHP/PHP-CS-Fixer/blob/v3.10.0/src/Fixer/Basic/NonPrintableCharacterFixer.php#L58-L64), originally created by [Ivan Borzenkov](https://github.com/ivan1986).

The files in [`demo/day-one/`](demo/day-one/) are taken from [Importing data to Day One: Details about the import file types](https://dayoneapp.com/guides/settings/importing-data-to-day-one/#details-about-the-import-file-types-), and can be downloaded [here](https://bloom-documentation.s3.amazonaws.com/JSON+Export+example.zip)

## Social

Follow [@localheinz](https://twitter.com/intent/follow?screen_name=localheinz) and [@ergebnis](https://twitter.com/intent/follow?screen_name=ergebnis) on Twitter.
