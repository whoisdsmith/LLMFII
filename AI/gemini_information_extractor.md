---
aliases:
  - gemini-information-extractor
tags:
  - "#streamlit"
  - "#gemma"
  - "#image-generation"
  - "#open-source"
  - "#api"

  - "#image-extraction"
  - "#google-gemini"
  - "#frontend-development"
---
## Info-Extractor  
A simple image information extractor app built using Google's gemini-vision-pro API and streamlit as front-end.

Install:
---
1. Clone the directory to your local environment

    ```
    git clone https://github.com/dvp-git/gemini-information-extractor.git
    ```
2. Change directory to *gemini-information-extractor* and install the necessary libraries using requirements.txt. Note: Use the latest version of python, preferably >=3.10

   ```
   pip install -r requirements.txt
   ```
4. Create a folder called *.streamlit* in your project directory and a file called *secrets.toml* inside it. Save your key as *GOOGLE_API_KEY="insert-your-key-here"* inside the toml file . Replace the *'insert-your-key-here'* with your own api key. This key is required to run the inference for generation of content.
5. Run the streamlit app as :

   ```
   streamlit run gemini_.py
   ```
   
For information on getting a key check: https://ai.google.dev/ 

Usage:
---
**NOTE: Do NOT upload any confidential documents as it may be retained by the system.**

The app is hosted on : https://gemini-information-extractor-9hvvirtqtzkvdt7ypmv9ju.streamlit.app/
You can either check the app there or follow the install steps  and use it in your local environment.

Application inputs:
- *Input Prompt*: The area represents the kind of information you'd like to extract from the image. This is optional in which case you'd get a simple description of the image.
- *Browse files* : Upload the file from which you want to extract information. Use jpg, jpeg or png format.
- *Generate* : Click this button to generate the information extracted.

Example 1: No input prompt
![image](https://github.com/dvp-git/gemini-information-extractor/assets/43114889/531b0977-0c37-478f-aef8-c0f13765015c)

If you do give an input prompt, you will receive the information you requested.

![image](https://github.com/dvp-git/gemini-information-extractor/assets/43114889/8d86d3e5-1aa5-4a86-b54f-1ed6694deb7e)

Streamlit is a powerful tool for building frontend in a short amount of time. 
You can create powerful applications using LLM's from google or HuggingFace and even LangChain . Models on HuggingFace can even be downloaded to your local environment , incase you do not wish to send your information to an API. 

Resources :
---
https://ai.google.dev/ 
https://docs.streamlit.io/get-started/fundamentals/main-concepts
https://docs.streamlit.io/library/cheatsheet


