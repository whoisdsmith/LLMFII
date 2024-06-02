---
aliases:
  - whispertranscribe
tags:
  - ai
  - whisper
  - openai-whisper
---
# whispertranscribe

An R-based tool that uses Open-AIs `whisper` to create transcripts from audio.

## Shiny app and R-file

There are two ways how to use `WhisperTranscribe`. Please see the requirements
first, before running the applications.

### 1. Shiny Application
There is a shiny application in the `WhisperTranscribe` sub-folder. The app is 
located in the single `app.R` file. By running this file the shiny app should 
load.


### 2. R-File
The file `transcribe.R` converts all file with the provided extension in the
input folder into transcripts in the output folder.


## Requirements

WhisperTranscribe needs Python + the Open-AI library. The setup file should 
install both of these.
If you don't want to use the sandbox environment of reticulate you can install 
the required library using pip as follows:

```
pip install -U openai-whisper
```

### Troubleshooting
See here https://github.com/openai/whisper for extended troubleshooting.

Whisper needs `ffmpeg` to understand different audio formats.
```
# on Ubuntu or Debian
sudo apt update && sudo apt install ffmpeg

# on Arch Linux
sudo pacman -S ffmpeg

# on MacOS using Homebrew (https://brew.sh/)
brew install ffmpeg

# on Windows using Chocolatey (https://chocolatey.org/)
choco install ffmpeg

# on Windows using Scoop (https://scoop.sh/)
scoop install ffmpeg
```



If you are using conda and cannot find ffmpeg, it helps to directly install ffmpeg from the conda command line in the bin directory of the conda-environment by calling `conda install ffmpeg` in the directory given by `pyconfig()` from the `test.R`.