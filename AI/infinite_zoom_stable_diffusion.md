---
aliases:
  - infinite-zoom-stable-diffusion
tags:
  - stable-diffusion
  - image-generation
  - ai-art
---
# Infinite Zoom Stable diffusion

## A colab notebook to generate infinite loop videos in minutes 
it works on free colab plan
 
<a target="_blank" href="https://colab.research.google.com/github/v8hid/infinite-zoom-stable-diffusion/blob/main/infinite_zoom_gradio.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>  👈 Easy to use notebook 

>built with gradio, with a nice UI

<a target="_blank" href="https://colab.research.google.com/github/v8hid/infinite-zoom-stable-diffusion/blob/main/smooth_infinite_zoom.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>  👈 Advanced notebook

>for more access and experimenting

### **[automatic1111 webui extention](https://github.com/v8hid/infinite-zoom-automatic1111-webui)** 👈

## Examples:

The painting:


https://user-images.githubusercontent.com/62482657/230250573-736e5630-571c-42da-9c3f-bb32d291a026.mp4



A psychodelic jungle:

https://user-images.githubusercontent.com/62482657/226931075-92b5e01d-0f1a-4259-be99-1895463e5caf.mp4



Dream of a Distant Galaxy:

https://user-images.githubusercontent.com/47415815/220372351-76a8b510-a42c-4025-99d3-9b6976cf10c4.mp4

<br>


### Credits

 - Original idea and 1st version of the notebook was created by [hardmaru](https://github.com/hardmaru)
 - Thereafter [BalintKomjati](https://github.com/BalintKomjati) made the following improvements:
    - Adapted to run on Google Colab
    - Introduced "interpolation" between outpainted images to create smoother videos. This allows to use wider outpainting masks which tend to generate larger coherent structures, without unpleasant jumps between frames.
    - Put the whole product into a intuitive, user friendly notebook (at least that was the intention :) )
 - Then [Vahid](https://github.com/v8hid) made the UI better and added a local version:
    - improved UI using Gradio
    - added some features including custom init image, multiple prompt feature, other models, etc.
    
### Do you want to contribute ?
What are you waiting for? create a pull request.
