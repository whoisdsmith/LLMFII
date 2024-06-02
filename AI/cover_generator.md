---
tags:
  - "#stable-diffusion"
  - "#openai"
  - "#gpt"
  - "#text-generation"
  - "#image-generation"

  - "#cover-generation"
  - "#dalle"
  - "#whisper"
---
<h1 align="center">
Cover Generator
</h1>
<h3 align="center">
  🎶 ➡ 🧠  ➡ 🖼️
</h3>

## Update 
The discussed pipeline can also be effectively applied to the cover generation of books, podcasts, music albums, meetings, documents, story books, and theatre scripts, as in serving a multi-purpose role. 

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href = "#description">Description</a></li>
    <li><a href = "#generates-music-album-covers-using-latest-ai-tools-namely">Our Approach with AI Tools</a></li>
    <li><a href = "#final-python-script">Pyhon Script</a></li>
    <li><a href = "#websites-deployed">Websites Deployed</a></li>
    <li><a href = "#papers-reviewed">Papers Reviewed</a></li>
  </ol>
  </summary>
</details>

## Description
<img src="https://github.com/Pushkar1853/Music-Cover-generator/blob/5918290f9ce9b4ed905d118e958d6a8ccadf4b8c/images/Abbey-Road-Cover.jpg" alt="your_alt_text" align="right" style="width: 50%; height: 60%;">
* This is a simple application that uses the spectacular Stable Diffusion model to generate images from song lyrics.

* We apply a large multilingual language model in open-ended generation of English song lyrics, and
evaluate the resulting lyrics for coherence and creativity using
human reviewers. 
* We find that current computational metrics for evaluating large language model outputs
have limitations in evaluation of creative writing. We note
that the human concept of creativity requires lyrics to be
both comprehensible and distinctive — and that humans assess certain types of machine-generated lyrics to score more
highly than real lyrics by popular artists.
* Inspired by the inherently multimodal nature of album releases, we leverage
a English-language stable diffusion model to produce high quality lyric-guided album art, demonstrating a creative approach for an artist seeking inspiration for an album or single.

## Pipeline
<img src="https://github.com/Pushkar1853/Cover-Generator/blob/e6551e1f187d744dbcfaf835789b1e0430b3cdf6/images/flow-covergen.jpg" alt="your_alt_text" style="width: auto; height: auto;">

## Generates music album covers using Latest AI tools, namely
<img src = "images\preface.png" align="center" style="width: 100%; height: auto;">
 <h3>1.  Stable Diffusion and DALL·E </h3>
 
- We’ve trained a neural network called DALL·E that creates images from text captions for a wide range of concepts expressible in natural language. DALL·E is a 12-billion parameter version of GPT-3 trained to generate images from text descriptions, using a dataset of text–image pairs. We’ve found that it has a diverse set of capabilities, including creating anthropomorphized versions of animals and objects, combining unrelated concepts in plausible ways, rendering text, and applying transformations to existing images.

- Like GPT-3, DALL·E is a transformer language model. It receives both the text and the image as a single stream of data containing up to 1280 tokens, and is trained using maximum likelihood to generate all of the tokens, one after another.

- This training procedure allows DALL·E to not only generate an image from scratch, but also to regenerate any rectangular region of an existing image that extends to the bottom-right corner, in a way that is consistent with the text prompt.
<img src = "images\stable-diffusion-text-to-image.png" align="center" style="width: 80%; height: auto;">
<img src = "images\stable-diffusion-unet-steps.png" align="center" style="width: 80%; height: auto;">

### How are lyrics transcribed?
This notebook uses openai's recently released 'whisper' model for performing automatic speech recognition. OpenAI was kind enough to offer several different sizes of this model which each have their own pros and cons. This notebook uses the largest whisper model for transcribing the actual lyrics. Additionally, we use the smallest model for performing the lyric segmentation. Neither of these models is perfect, but the results so far seem pretty decent.

  <h3>2. OpenAI Whisper for transcript </h3>
  
* Whisper is an automatic speech recognition (ASR) system trained on 680,000 hours of multilingual and multitask supervised data collected from the web. We show that the use of such a large and diverse dataset leads to improved robustness to accents, background noise and technical language. Moreover, it enables transcription in multiple languages, as well as translation from those languages into English. We are open-sourcing models and inference code to serve as a foundation for building useful applications and for further research on robust speech processing.

  <img src = "images\whisper.png" style="width: 80%; height: auto;">
  
* The Whisper architecture is a simple end-to-end approach, implemented as an encoder-decoder Transformer. Input audio is split into 30-second chunks, converted into a log-Mel spectrogram, and then passed into an encoder. A decoder is trained to predict the corresponding text caption, intermixed with special tokens that direct the single model to perform tasks such as language identification, phrase-level timestamps, multilingual speech transcription, and to-English speech translation.

<h3> 3. Chat GPT and GPT-2 models </h3>

* We trained this model using Reinforcement Learning from Human Feedback (RLHF), using the same methods as InstructGPT, but with slight differences in the data collection setup. We trained an initial model using supervised fine-tuning: human AI trainers provided conversations in which they played both sides—the user and an AI assistant. We gave the trainers access to model-written suggestions to help them compose their responses. We mixed this new dialogue dataset with the InstructGPT dataset, which we transformed into a dialogue format.

* To create a reward model for reinforcement learning, we needed to collect comparison data, which consisted of two or more model responses ranked by quality. To collect this data, we took conversations that AI trainers had with the chatbot. We randomly selected a model-written message, sampled several alternative completions, and had AI trainers rank them. Using these reward models, we can fine-tune the model using Proximal Policy Optimization. We performed several iterations of this process.

<img src ="https://github.com/Pushkar1853/nanoGPT/blob/1460e488f1049b8b151408db495531b1852fc41a/images/ChatGPT_Diagram.svg"  style: height="600px" width="auto" align="right" >

## <h2> Notebooks: </h2>

The whole process is divided into three sections:
* <h3> The generation of Lyrics/Transcript from given audio file </h3>  
[For notebook of meeting audio  --->  Transcript](https://github.com/Pushkar1853/Music-Cover-generator/blob/32e4240fadb609a657a8595ebe6d6d396f65cb42/final-baseline/meeting-audio-lyrics.ipynb)

[For notebook of music audio  --->  Lyrics](https://github.com/Pushkar1853/Music-Cover-generator/blob/64214eef0ddf54eed3139e6b1017db66ee8d20ac/final-baseline/music-audio-lyrics.ipynb)

* <h3> The generation of Prompt from the lyrics </h3> 
[For notebook of lyrics  --->  prompt](https://github.com/Pushkar1853/Music-Cover-generator/blob/32e4240fadb609a657a8595ebe6d6d396f65cb42/final-baseline/lyrics-prompt.ipynb)

* <h3> The generation of Stable-diffused image from the Prompt </h3> 
[For notebook of prompt  --->  image](https://github.com/Pushkar1853/Music-Cover-generator/blob/32e4240fadb609a657a8595ebe6d6d396f65cb42/final-baseline/prompt-image.ipynb)

## <h2>Final Python Script</h2>

[Python Script - Click here](https://github.com/Pushkar1853/Music-Cover-generator/blob/6f2eece3127839d59758b8e53aa4a8409fa0fc6a/scripts/meeting_cover_baseline.py)

` scripts/meeting_cover_baseline.py `

## <h2> Notebook for creation of meeting/book/document covers using transcript</h2>

[Meeting/Book/Document covers notebook - click here](https://github.com/Pushkar1853/Music-Cover-generator/blob/32e4240fadb609a657a8595ebe6d6d396f65cb42/final-baseline/meeting-cover-baseline.ipynb)

` final-baseline/meeting-cover-baseline.ipynb `

## <h2> Notebook for creation of music covers using lyrics</h2>

* [Music cover notebook - Click here](https://github.com/Pushkar1853/Music-Cover-generator/blob/64214eef0ddf54eed3139e6b1017db66ee8d20ac/final-baseline/music-cover-baseline.ipynb)

` final-baseline/music-cover-baseline.ipynb `

* [Podcast cover notebook - Click here](https://github.com/Pushkar1853/Music-Cover-generator/blob/5b5f84dc2f60815691789a4acf9d78175859aad8/final-baseline/meeting-final-pipeline.ipynb)

` final-baseline/meeting-final-pipeline.ipynb `

## <h2>Websites deployed</h2>

* [Cover-Gen text-to-image](https://huggingface.co/spaces/PushkarA07/Cover-Gen-text2img)
* [text-to-image webapp.py](https://github.com/Pushkar1853/Music-Cover-generator/blob/6f2eece3127839d59758b8e53aa4a8409fa0fc6a/webapp/app.py)
* [Cover-Gen audio-to-image](https://huggingface.co/spaces/PushkarA07/Cover-Gen-audio2image)
* [audio-to-image webapp.py](https://github.com/Pushkar1853/Music-Cover-generator/blob/6f2eece3127839d59758b8e53aa4a8409fa0fc6a/webapp/app2.py)

## Papers reviewed:
* [High-Resolution Image Synthesis with Latent Diffusion Models](https://arxiv.org/abs/2112.10752)
* [Robust Speech Recognition via Large-Scale Weak Supervision](https://cdn.openai.com/papers/whisper.pdf)
* [In BLOOM: Creativity and Affinity in Artificial Lyrics and Art](https://www.researchgate.net/publication/367165610_In_BLOOM_Creativity_and_Affinity_in_Artificial_Lyrics_and_Art)
<img src="https://github.com/Pushkar1853/Music-Cover-generator/blob/eb1c8fc1bd521b27116554f39df0891aa988189d/images/chin1.png" style="width: 50%; height: 60%;">

* [GLIGEN, Open-Set Grounded Text-to-Image Generation](https://www.researchgate.net/publication/367216711_GLIGEN_Open-Set_Grounded_Text-to-Image_Generation) 

Large-scale text-to-image diffusion models have madeamazing advances. However, the status quo is to usetext input alone, which can impede controllability. In thiswork, we propose GLIGEN,Grounded-Language-to-ImageGeneration, a novel approach that builds upon and extendsthe functionality of existing pre-trained text-to-image dif-fusion models by enabling them to also be conditioned ongrounding inputs. To preserve the vast concept knowledge ofthe pre-trained model, we freeze all of its weights and injectthe grounding information into new trainable layers via agated mechanism. Our model achieves open-world groundedtext2img generation with caption and bounding box condi-tion inputs, and the grounding ability generalizes well tonovel spatial conﬁgurations and concepts. GLIGEN’s zero-shot performance on COCO and LVIS outperforms existingsupervised layout-to-image baselines by a large margin

<img src="https://github.com/Pushkar1853/Music-Cover-generator/blob/eb1c8fc1bd521b27116554f39df0891aa988189d/images/pap2.png">
