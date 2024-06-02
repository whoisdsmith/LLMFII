---
aliases:
  - Textify-text-Preprocessing
tags:
  - "#python"
  - "#nlp"
  - "#text-generation"
  - "#flask"
  - "#huggingface"

  - "#text-preprocessing"
  - "#text-summarization"
  - "#web-application"
---
# Textify-A Text Preprocessing Web Application
## A text preprocessing web application which helps a user to get the summary of an Article and also a text generator which generates text based on user input

### Technologies used
+ [Flask](https://flask.palletsprojects.com/en/2.0.x/) (**A micro web Framework**)
+ [nltk](https://www.nltk.org/) (**Python Library**)
+ [Hugging Face GPT-2](https://huggingface.co/gpt2) (**For text generation**)
+ [HTML,CSS,JS](https://www.w3schools.com/whatis/) (**Core technologies for building webpages**)
+ [Python](https://www.python.org/) (**Programming language For Backend**)
+ [Pytorch](https://pytorch.org/) (**For text generation**)
+ [Tensorflow](https://www.tensorflow.org/) (**An end-to-end open source machine learning platform**)
---
## Working of this application
Firstly the Application is Command line based executable under Python Environment and uses popular Python micro web framework that is FLASK.This Application consist of 2 main pages runs in LocalHost wherein intially a form is given to the user based on the content entered and on submit by the user,Accordingly the Summarizied Content is analyzed with support and importing of some python packages.This data is exported to the next connecting page.

**For text generation**
Hugging Face is an NLP focused startup that shares a large open-source community and provides an open-source library for Natural Language Processing. Their core mode of operation for natural language processing revolves around the use of Transformers. This python based library exposes an API to use many well-known architectures that help obtain the state of the art results for various NLP tasks like text classification, information extraction, question answering, and text generation. All the architectures provided come with a set of pre-trained weights utilizing deep learning that help with ease of operation for such tasks.These transformer models come in different shape and size architectures and have their ways of accepting input data tokenization. A tokenizer takes an input word and encodes the word into a number, thus allowing faster processing.

**Tokenizer in Python**
In both of the text processing part tokenizer is playing a vital role. In Python tokenization basically refers to splitting up a larger body of text into smaller lines, words or even creating words for a non-English language. The various tokenization functions in-built into the nltk module itself and can be used in programs as shown below.
 

## This Project Comprises of 3 Modules namely
+ Landing Page
+ Summarized Content as Output
+ Text Generation as Output

Run the these Commands in the Windows Terminal:

**Note Before Running the text-summarisation run these commands**

`pip install nlp`

**For exporting and processing the data,run the following script in new .py file before ruuning the application as follows:**

```python
   import nltk
   nltk.download('stopwords')
   nltk.download('word_tokenize')
   nltk.download('sent_tokenize')
```
**In order to run and intialize the application there are 2 alternative methods:**
+ Method - 1 : Run from Editor in venv and view localhost application in any Browser with link 
(http://127.0.0.1:5000/)
+ Method - 2 : Run from command prompt with specified path location of project by using following command

```
 python __init__.py
```
**Landing Page**

![alt text](https://github.com/VivekChoudhary77/Textify-text-preprocessing/blob/master/Images/Screenshot%20(6).png)

**Summarisation** (**Before Summarisation**)

![alt text](https://github.com/VivekChoudhary77/Textify-text-preprocessing/blob/master/Images/Screenshot%20(7).png)

**Output** (**Summarised content of Article**)

![alt text](https://github.com/VivekChoudhary77/Textify-text-preprocessing/blob/master/Images/Screenshot%20(8).png)

---
### For the Text generation Part

**Run these commands before running the Text Generation**

```python
 pip install tensorflow
 pip install transformers
 pip3 install torch torchvision torchaudio
```

**For Conda**

`conda install pytorch torchvision torchaudio cpuonly -c pytorch`

**Note : While Running the text generator part the model will automatically download the required files for text generator i.e. GPT2 Model**

**Some terms and their meaning in the project**

+ **_max_length_** : Outputs the no. of words you want to see while generating the text.
+ **_input_ids_** : Indices of input sequence tokens in the vocabulary.
+ **_pad_token_id_** : If a pad_token_id is defined in the configuration, it finds the last token that is not a padding token in each row.
+ **_num_beans_** : bean search to find the next appropriate words in the sequence.
+ **_no_repeat_ngram_size_** : Stops repeating certain sequences over and over again.(Basically it stops our model repeating words or sentences).
+ **_early_stopping_** : if model does not genrates more or great output it generally stops generating the output.
+ **_skip_special_tokens_** : always be **True** because we want to return sentences not the endofsentence tokens and other tokens we only want the words.
+ **_return_tensors_** : 'pt' refers as pytorch tensors.

---

**Text-Generator** (**landing page**)

![alt_text](https://github.com/VivekChoudhary77/Textify-text-preprocessing/blob/master/Images/Screenshot%20(9).png)

**Text-Generator** (**Output**)

![alt_text](https://github.com/VivekChoudhary77/Textify-text-preprocessing/blob/master/Images/Screenshot%20(10).png)

---

**_So here it Concludes the project by generating the output by matching the keywords what user has entered_.**
