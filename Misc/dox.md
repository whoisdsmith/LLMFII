---
aliases:
  - dox
tags:
  - markdown
  - opensource
  - cli
  - "#documentation"
  - "#cli"
  - "#software-development"
  - "#api"
  - "#opensource"

  - "#document-indexing"
  - "#flutter"
  - "#rust"
---
<div align="center">

  <h1><code>dox</code></h1>

  <h3>
    <strong>DOcuments indeXer</strong>
  </h3>

  <table>
    <tr>
      <th>core</th>
      <th>client</th>
    </tr>
    <tr>
      <td>
        <p>
          <img src="https://img.shields.io/github/actions/workflow/status/devzbysiu/dox/core-ci.yml?style=for-the-badge" alt="Core CI status badge" />
        </p>
      </td>
      <td>
        <p>
          <img src="https://img.shields.io/github/actions/workflow/status/devzbysiu/dox/client-ci.yml?style=for-the-badge" alt="Core CI status badge" />
        </p>
      </td>
    </tr>
  </table>

  <p><img src="https://img.shields.io/badge/license-MIT%2FAPACHE--2.0-blue?style=for-the-badge" alt="License"/></p>
  <h3>
    <a href="#about">About</a>
    <span> | </span>
    <a href="#demo">Demo</a>
    <span> | </span>
    <a href="#installation">Installation and Configuration</a>
    <span> | </span>
    <a href="#license">License</a>
    <span> | </span>
    <a href="#contribution">Contribution</a>
  </h3>

  <sub><h4>Built with 🦀 and <img src="./assets/flutter.png" width="17" alt="flutter icon"></h4></sub>
</div>

# <p id="about">About</p>

> :warning: This is still in progress and undergoes heavy refactoring, so it should be considered
unstable.

One of the most frustrating activities I had to do from time to time is to search through a pile
of documents to find the one I'm looking for. Wouldn't be better to just open an app and type
keywords in the s[core](../_FileOrganizer2000/Inbox/core.md)That's what this project is for. TLDR: you install a [core](./core) on your PC. Through the
configuration file, you tell it which directory should be watched for new files. Every time new
file appears, core will extract the text from the file and index it.

You also install [client](./client) app on your smartphone. It allows you to list and search
scanned files. It also allows scanning new documents by using a camera or just picking a PDF.

# <p id="demo">Demo</p>

## --- TODO ---

# <p id="installation">Installation and configuration</p>

## Core
1. Go to [releases](https://github.com/devzbysiu/dox/releases) and download binary for your system.
2. Run `dox init`. It will display a CLI, so you can configure it:
  1. `watched_directory` - a directory which is monitored for new files. If you are going to scan
     documents through your printer, use the directory to which your printer is saving scanner files.
  2. `index_dir` - directory holding and indexed text.
  3. `cooldown_time` - time after which the buffered files will be indexed.
3. After configuration, the `dox` server will be exposed on port `8000`. Keep this in mind, you'll need
   to point the client to the `dox` server

## Client
--- TODO ---
1. Go to [releases](https://github.com/devzbysiu/dox/releases) page and download APK file.
2. Install it on your device.
3. Run the app. On first run, it will show you settings page:
  - `dox address` - the address of the dox server
  > **NOTE**: the dox server needs to be accessible to the client. If you are setting the core
  on local machine, make sure that the phone is on the same network as the local machine.

# <p id="license">License</p>

This project is licensed under either of

- Apache License, Version 2.0, (LICENSE-APACHE or http://www.apache.org/licenses/LICENSE-2.0)
- MIT license (LICENSE-MIT or http://opensource.org/licenses/MIT)

at your option.

# <p id="contribution">Contribution</p>


Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the
work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any
additional terms or conditions.
