---
aliases:
  - augment_audio_tools
---
# Audio Augmentation Tools for Machine Learning

This script provides a set of audio augmentations for machine learning purposes, in particular useful for the RAVE model https://github.com/acids-ircam/RAVE . It allows you to process audio files by changing their speed, resampling, splitting stereo files into mono, adding silence, and creating chunks.

## Features

- Change speed of the audio file
- Resample the audio file
- Split stereo files into mono
- Add silence to the audio file
- Create chunks of the audio file

## Requirements

- Python 3.6 or higher
- NumPy
- SoundFile
- Resampy

To install the required packages, you can run:

```bash
pip install numpy soundfile resampy
```

## Usage

To use this script, run it from the command line with the following arguments:

```
python augment_audio_speed.py <input_folder> <output_folder> [--chunk_duration] [--split_stereo] [--add_silence] [--speed_change]
```

- `input_folder`: Path to the input folder containing audio files
- `output_folder`: Path to the output folder for processed files
- `--chunk_duration`: (optional) Duration of each chunk in seconds (default: 30 seconds)
- `--split_stereo`: (optional) Split stereo files into two mono files
- `--add_silence`: (optional) Length of silence in seconds added to the end of each sound file
- `--speed_change`: (optional) Speed change factor 0.0-0.9 (default: 0.0, no change)

Example:

```bash
python augment_audio_speed.py input_folder output_folder --chunk_duration 30 --split_stereo --add_silence 1.5 --speed_change 0.1
```

This will process all supported audio files in the `input_folder` and save the processed files to the `output_folder` with specified augmentations.

## Supported Audio Formats

The script supports the following audio file formats:

- .wav
- .flac
- .ogg
- .aiff
- .mp3