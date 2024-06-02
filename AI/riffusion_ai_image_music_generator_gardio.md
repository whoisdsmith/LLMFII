---
aliases:
  - Riffusion_AI_Image_Music-generator_Gardio
tags:
  - python
  - stable-diffusion
  - audio-processing
---
# Riffusion AI music & Image generator(Gardio)
This code includes a collection of tools for processing audio files and generating AI music from Stable Diffusion images with Gardio.
![Screenshot_20230103_053151](https://user-images.githubusercontent.com/52294485/210404128-48073aeb-8493-4d93-9309-5ad5a7ce72f4.png)
# Requirements
The following libraries are required to use the code in this repository:

`numpy
PIL
pydub
scipy
torch
torchaudio`
### Recommended: Running in [Google Colab.](https://colab.research.google.com/)
This project can be run in a Google Colab notebook. To open the notebook in Colab, click the "Open in Colab" button at the top of this page, or follow these steps:

1. Go to the Google Colab homepage.
2. Click the "Upload" button in the top right corner of the page.
3. Select the notebook file from your computer and click "Open."
4. The notebook will open in a new tab in your browser, and you can run the code cells by clicking on them and then clicking the "Run" button on the left.

# Installation
To install the required libraries, run the following command(cells available in the notebook):

`!pip install -q https://github.com/camenduru/stable-diffusion-webui-colab/releases/download/0.0.15/xformers-0.0.15.dev0+189828c.d20221207-cp38-cp38-linux_x86_64.whl`<br>
`!pip install -U transformers diffusers gradio ftfy pydub -q`

# Usage
Functions for processing audio files and converting between spectrogram images and waveforms are as follows:
- `wav_bytes_from_spectrogram_image`: converts a spectrogram image to a waveform in WAV format
- `spectrogram_from_image`: converts a spectrogram image to a spectrogram array.
- `image_from_spectrogram`: converts a spectrogram array to a spectrogram image.
- `waveform_from_spectrogram`: converts a spectrogram array to a waveform.
- `spectrogram_from_waveform`: converts a waveform to a spectrogram array.

To use these functions, import the necessary modules and then call the desired function with the appropriate arguments. 


### Credits goes to the [riffusion project](https://github.com/riffusion/riffusion) and [amrrs's ai-music-video](https://github.com/amrrs/ai-music-video/blob/main/Riffusion_%2B_Gradio_AI_Generated_Music_Video.ipynb).

##### This code is released under the MIT License. See LICENSE for more details.
