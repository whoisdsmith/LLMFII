---
tags:
  - "#rust-tool"
  - "#software-development"
  - "#developer-tools"
  - "#open-source"

  - "#document-management"
  - "#vuejs"
  - "#tauri"
---
# FileSpider

![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/kruemmelspalter/filespider/build.yml)
![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/kruemmelspalter/filespider/tests.yml?label=tests)
![GitHub](https://img.shields.io/github/license/kruemmelspalter/filespider)
![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/kruemmelspalter/filespider)
![GitHub release (latest SemVer including pre-releases)](https://img.shields.io/github/v/release/kruemmelspalter/filespider?include_prereleases)
![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/kruemmelspalter/filespider)

FileSpider is a software for organizing and editing documents.
Documents consist of a main file and optionally different assets like images.
For example:

- a Markdown document
- an HTML document with audio files embedded
- a LaTeX document split into multiple other tex files and also images
- a Xournal++ stylus note

These documents are organized via tags that can be searched for (positive and also negative filters)
For example:

- done homework in CS about Java: `school,homework,done,cs,java` (could also be simplified to `done,cs,java` in most
  cases but the filter before should always be correct)
- homework that's still to do in German: `school,homework,german`
- a notebook entry in English about literature: `notebook,english,literature,school`

Example searches:

- `school`: matches all documents with the tag `school` -> All stuff related to school
- `homework,cs`: matches all documents with tags `cs` and `homework` -> All CS homework
- `homework,!done`: matches all documents with the tag `homework` and without the tag `done`-> All homework that still
  needs to be done

The documents are rendered in a specified way, for example:

- LaTeX files are rendered using pdflatex
- HTML files and images are just served plainly
- Markdown is rendered using pandoc and uses KaTeX for math

## Used Technologies

### Backend

The backend is written in Rust and uses the [tauri](https://tauri.app/) framework for the GUI. It uses a SQLite 3
database for storing document metadata and `sqlx` for database access. The documents are stored in a directory that
defaults to `~/.local/share/filespider/`. They are rendered with various renderers depending on the document type and
being stored in the `.cache` directory in the document directory.

### Frontend

The frontend is written in Vue.js and uses Vuetify.js for the UI components.

## Supported Platforms

Currently, only Linux is supported. Windows is not supported as the hashing library is not Windows compatible, but I
will soon replace it and make the app Windows compatible (see #87). I'm not sure about macOS as I don't have any Mac
device to test it on.

## Setup

Launch the AppImage or install the deb package and launch the application.

### Development Setup

Use `cargo tauri dev` for an auto-reloading development server

## Usage

- Use the `Create Document` button to create a new document
- If there already are documents, search for a document via entering appropriate tags or a crib (still requires at least
  one tag) in the search bar

