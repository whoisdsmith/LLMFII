---
tags:
  - "#chatgpt"
  - "#prompt-engineering"
  - "#data-analysis"
  - "#custom-instructions"
  - "#ai"

  - "#data-distillation"
  - "#advanced-data-analysis"
  - "#personalization"
---
# DATA DISTILLATION
### A prompt-engineering technique for creating personalized custom instructions on ChatGPT

![Modern Western-anime hybrid style animated male character with a slight tan, chiseled jawline, short pointed dark hair styled in a slight mohawk, thick angular eyebrows, striking yellow eyes, short pointed beard and mustache, wearing a high-collared dark gray cloak with fur lining. This character intently examines a glowing, translucent flask containing a luminescent liquid in a rustic, dimly lit alchemical laboratory. The room is filled with stone walls, a wooden window with a diamond-patterned lattice, and an assortment of alchemical tools, apparatuses, and ingredients. He's surrounded by a large distillation apparatus, wooden shelves holding glass containers, and a wooden bench providing a workspace.](TechniqueImg.png)
>Image Generated via DALL-E 3

## INTRODUCTION:

Welcome to the first prompting how-to guide in my Prompt Alchemy series! This is my first attempt at sharing some of my prompt "engineering” techniques, tips, and tricks, so if you like this repo, please consider giving it a star or forking it to contribute. You can also share it within your network to help others find it! I’m more than happy to share more if folks are interested. 

This guide should allow you to have more personalized interactions with ChatGPT leveraging successful conversations you’ve had with it before to create specialized prompts inside the “custom instructions” settings in ChatGPT. I call this data “distillation” and not something like “summarization” or “optimization”, because the key here is not to retain the same context or structure, but to condense and transform data into something that is more suitable for this use case. 

Keep in mind that this is aimed at using *your own* data to work with through this process with GPT. The intention is to produce a personalized output for personal use. If you are not comfortable letting GPT work with such a dataset and the contents inside it, then this technique is likely not for you. Adapting this framework to handle alternative uses from other data (that you own) will have to be done by yourself. 

I hope you find this guide helpful! 

| ⚠️ NOTE: | This technique requires access to the “Advanced Data Analysis” plugin.  |
|-------|-------------------------------------------------------------------------|

| ⚠️ NOTE: | This technique is designed for the ChatGPT web UI only.  Files cannot be directly given to the GPT models via CLI (yet).   |
|-------|-------------------------------------------------------------------------|

This technique aims to distill personal conversation data into something that fits in the “custom instructions” setting on the ChatGPT interface. It’s likely possible to utilize this method for API calls as well, however, keep in mind you still need access to the Advanced Data Analysis plugin on the ChatGPT interface to use this technique. For the purposes of this demonstration, I assume you will be using what’s exported from ChatGPT’s website.

This is not going to be a single-shot prompt. Think of this as a demonstration of prompt “guidance”, more closely resembling CoT reasoning, although slightly different. Chunking and processing this in reasonable, actionable steps is vital for achieving the desired results effectively and efficiently. If you expect it to do everything all at once, it’s going to get confused and forget all of the details it was supposed to include and do.


## PART I: GATHERING & OPTIMIZING THE DATA

You can gather and format your personal data from this step-by-step list.

  1.	Export your data from ChatGPT’s website via the ‘settings’ tab. You should receive an email shortly after, which gives you a 24-hour window to download. I’d recommend exporting it on a weekday: for some reason, when you send the request on a weekend, it doesn’t always go through.
  2.	Unzip the file. We will be using “conversations.json” for this technique, so extract that file and place it somewhere safe. 
  3.	Go to ChatGPT, select “Advanced Data Analysis” and upload the file. In the prompt, request `“Could you pretty-print or reformat the entire json file to a more human-readable format and allow me to download the reformatted file?” ` Save this file where you saved the original conversations file. GPT has a harder time interpreting how to handle the json file and gets stuck if it isn’t pretty-printed. When it’s reformatted this way, GPT can quickly and easily assess the file and its contents. 
  5.	With updated file in hand and GPT primed in turn, we are ready to begin the analysis phase and ask GPT for what we want.


## PART II: CONDUCTING THE ANALYSIS FOR DISTILLATION

You can approach this in one of two ways: You can explain the goals and intentions of what you’re trying to accomplish first and allow GPT to generate the analysis stages itself (which is what I did, with cross-referencing), or you can specifically request the analysis in the stages I provide below. Keep in mind that my background is in linguistics, so I can verify what analyses it’s attempting to conduct and refine what it tries to do based off my knowledge if it does something weird. To reduce friction and confusion, I’d recommend using my provided prompts, but if you’re explorative and curious like me, seeing what approaches it suggests could be a fun experience. 

Before we continue, understand that GPT will likely try to verify with you if what it does is right, and go over its steps. As many people rightly point out, you can’t expect outputs and outcomes to be identical each time you try it. Remain flexible during this process and provide as much constructive feedback as possible. My provided prompts *guide* the model to accomplish the task, I do not *command* it. Use the prompts but understand it will be up to you to guide it in the right direction to achieve the goal. This isn’t as hard as it sounds, because turning the analysis process into clear steps allows the model to respond step-by-step, response-by-response, allowing for periods of clarification and feedback to adjust when necessary. You may need to remind it of the final step if the conversation extends far, but again, a quick reference to “remember X?” redirects its attention to the intended goal.

It's a good idea to outline your intentions first before you consider what and how to prompt. Let’s go over that now. Below is a high-level overview of what we’re trying to do and how to do it.

### Overarching Goal: To create a personalized custom instruction set based off the conversation data in the dataset.

Steps: 
1.	Express intentions and overarching goal to GPT
2.	Conduct Analyses
a.	Step-by-step analysis instructions
3.	Retrieve outputs from analysis results
4.	Amalgamate results into the custom instruction format
   
Now, let’s construct the prompt to express our goal to GPT, and what we expect it to do:

>“This dataset that we are working with is my accumulated personal interaction data as a user.
>My overarching goal for this conversation is to concoct a set of custom instructions using this dataset to personalize future interactions and simultaneously simplify further instructions.”


If you would like GPT to generate its own instructions for achieving the goal, simply append this:


>“Could you help me achieve this and analyze my data?”

Asking for a confirmation check like this allows the AI to respond by both verifying its understanding of your prompt and proving it understood what you asked by explaining how it would accomplish this task, which typically occurs in a list-like fashion that’s easy to follow. You do not need to explicitly tell GPT to construct the analysis steps, because it will do that on its own here.

| ⚠️ CAUTION: | The addition to the prompt here does not need to be replicated verbatim, but the final clause MUST be an interrogative clause, and it MUST end its punctuation with a ‘?’ for the behavior to be replicated.    |
|-------|-------------------------------------------------------------------------|

If you would like to use the pre-built process, it can be replicated as follows. Append this to the original prompt:

>“In order to achieve this, let’s break this down into a step by step process. We can follow this method as follows:
>1.	Basic Statistics: We'll start by analyzing the number of conversations, average message length, frequency of interactions, etc.
>2.	Content Analysis: We'll delve into the content of the messages in this interaction data to understand topics of interest, frequently used phrases, sentiment, and more.
>3.	Interaction Patterns: We'll look at how you interact with the assistant, such as the types of questions you ask, feedback provided, formats, and the timing of interactions.
>4.	Custom Instructions Development: Based on insights from the above, we'll formulate custom instructions that can be used to streamline future interactions.
>
>Do you understand the instructions?”

These are metrics that GPT seems to value favorably.  While it might seem insignificant or irrelevant to us, remember we aren’t constructing these instructions for us to interpret, we’re constructing them for *the AI* to interpret. 

After this prompt is sent, it will begin going through the step-by-step process through a series of responses, trials, and errors. It is likely that each instruction step will be preceded by a sub-process of steps to accomplish the specific step’s goal. The amount of responses it takes to complete the sub-steps of a given super-step varies, but it should reach the correct results with little to no interference other than `“let’s proceed!”`.

To cross-check and verify the successful steps my iteration used to accomplish these tasks, I’ve provided them below. Don’t worry, I don’t expect everyone who uses this technique to know all of these fancy analyses and how they’re supposed to work.  You can use this as a reference to know what works and what to look for. If the AI suggests it wants to do something you don’t know or don’t understand, tell it to follow the steps below. You can also use the outline to match the sub-steps together to make sure it’s on the right track. Remember, this is an outline for guiding the model; I would not recommend sending this as a prompt verbatim to the model. 


<details>
  <summary><h3>1. Basic Statistics </h3></summary>
  
  1. #### Total number of conversations with assistant
  2. #### Total number of messages sent
  3. #### Average length of messages sent
  
</details>
<details>
  <summary><h3>2. Content Analysis </h3></summary>
  
  1. #### Topics of interest: keyword extraction and/or topic modeling
     1. If the model fails to achieve this, you can suggest an n-gram, omitting function words
  2. #### Frequently used phrases or words: use Latent Dirichlet Allocation (LDA)
     1. The results might look vague, but combined with other results, it’ll prove important in time.
  3. #### Sentiment analysis: Understanding user’s tone as generally positive, neutral, or negative.
     1. High positive and/or neutral Sentiments is ideal, although the amount of each will likely vary for all users. Having high counts in both typically indicates constructive and informational interactions.
     2. I do not know what would happen with a high negative sentiment. I’d recommend to let the AI analyze the data to identify areas of improvement if this occurs. Keep that info noted; it may be important for it to come back to later.
  4. #### Specific requests / questions frequently posed to the assistant
     1. I suspect this step is used to identify key repetitive syntax, so it can be implemented into custom instructions automatically by default.
  
</details>
<details>
  <summary><h3>3. Interaction Patterns </h3></summary>
  
  1. #### Message Flow: How do conversations typically flow? Do they involve back-and-forth exchanges, or are they more one-sided? The valuable metrics here are:
     1. Avg. number of Exchanges per conversation (are you a single-shot prompter, or do you have lengthy conversations with GPT?)
     2. Balance Ratio (For every assistant message, how many messages do you send?)
  2. #### Question Patterns: How often does the user pose questions, and what types of questions dominate (e.g., "how", "what", "why")?
     1. Total Question Count (remember, not every prompt is a question)
     2. Average Number of Questions per Message
     3. Most frequent types of questions
     4. Avg. Question Length
  3. #### Feedback: Do you provide feedback or corrections to the assistant’s responses?
     1. Positive Feedback (appreciating/complimenting the assistant)
     2. Constructive Feedback (providing suggestions or pointing out inaccuracies)
     3. Error Reporting (when you’ve explicitly told the assistant they made an error or didn’t understand)
  
</details>

Remember, GPT isn’t god, you may still need to remind it once or twice to keep on track and to follow the process. It may want to skip a step or two. Once you’ve successfully coaxed the model into responding with all of the analysis results above, and you can see its work, it’s time for the final phase. Don’t step away for long; if it times out, GPT will forget all of the data it acquired due to inactivity. You could try to request it to look back through the conversation, but depending on conversation length, is likely to prove unreliable. 

## PART III: DISTILLING THE RESULTS

 The results of the analysis have been acquired, and if guided properly, should have outputted all of the findings so far. You can leverage this for remembrance, retrieval, and verification by cross-checking the distilled instructions with the earlier provided results. Since this data was acquired using Advanced Data Analysis, you can go back and observe how it calculated these results. The numbers should have all been calculated programmatically via legitimate analysis techniques if you’ve followed by outline, meaning they are most likely accurate and non-trivial. GPT is able to summarize key chunks and assessments of data as well, so whatever is not a numerical value has been a direct result of summarizing the data analysis criteria. This is important, because when it distills the final results we want and the numbers don’t match (it happens), remind and refer it to the key data points it provided earlier (or, alternatively, copypasta them directly as an error correction).
Once you’re ready, it’s time to refer the model to the overarching goal, and provide GPT the clear, explicit instructions for what we want using the results we’ve acquired (that GPT should have hot-loaded for contextual reference if it did not timeout). 

If you notice earlier, we did not provide detailed, clear instructions about precisely what these custom instructions are and how we want them constructed and distilled. This was intentional in order to not overwhelm and/or misdirect GPT’s attention. What we’ve been doing up to this point has been refining the *context* of information that GPT can work with down to a manageable set of parts. Instead of condensing the context of the window by summarizing the data, we extract the most relevant parts of the data that matter to an AI. Now that we’ve extracted these details, we can use that as our context to create our distilled instruction set. 

> “Now, remember our overarching goal for this conversation. The goal for creating these custom instructions is to have the AI understand the kind of user I am quickly, and to create a personalized custom instruction set based off the entire interaction data we’ve analyzed thus far. This AI in question is you, specifically, on this platform. There are two boxes present. They are as follows:
>
> 1. What would you like ChatGPT to know about you to provide better responses?
> 2. How would you like ChatGPT to respond?
>
> Both boxes have a character limit of 1500. The challenge is that I want future interactions with GPT to know accurate information about our prior interactions and how I've been using this platform. You now have both statistical results and my raw conversation data to work with. I want the most accurate and well-tuned instructions possible that best condenses everything I've done with you so far effectively and efficiently. 
> I want to be clear as well, the best results do not need to be interpretable to me as a human. If it's best summarized as a seemingly nonsensical jumble of words or other some such data, that's fine so long as it is the best and most accurate way to condense as much of the information and intent as possible for the assistant to interpret. 
> Will this work for you?”

This prompt should be everything you need to have it provide the results you want. From this, it should provide you a detailed analytical summary of the key components of your data. Cross-check the numerical values with earlier results for verification, and refine as needed, asking to append any relevant information you think it missed. For my instance, it provided a two-step response process; one for each instruction box. 

Now, the key component to make this successful and effective is the second paragraph in the last prompt. This is what distinguishes a summarization technique from this distillation technique. When you summarize, the intention is to maintain a relative narrative and structure of the overall source material. Ideally, a summary should be a condensed version of the same thing. Here, our goal is slightly different. We wanted the most important parts of the data that would help an AI be better prepared for future interactions with as little contextual explanations as possible while minimizing repetitive questions or phrases (i.e. `“provide the output in a 5th-grade reading level”`), condensed into 1500 characters. The  trick is to leverage GPT by letting it provide those valuable insights itself, regardless of our ability to understand what it means or why it’s relevant to it. You must emphasize to GPT to allow this behavior and prioritize AI-interpretability over human-interpretability.  Therefore, this can be seen as a form of “distilling” the data, because we are transforming the result into something that’s structured and used differently than its source material, but cannot be created without the source material itself.

Congratulations, you’ve just performed Data Distillation! Enjoy much easier and smoother conversations with your assistant, with a lot less friction and a lot less repetitive instructions.

You can see the result for the first instruction below. This was not the final instruction; I did refine this this further and appended other personal optimizers, so I’m comfortable sharing this, as this was the immediate response. A couple values have been redacted, but this paints a picture of the result.  You can see from this data already how I use this platform and what the AI thinks is relevant for itself. Notice how long my conversations are. Recognize that quality prompting isn’t necessarily about turning everything into a single-shot prompt, but rather quality prompt *guidance* to achieve significant and interesting results. See how it compares to your result!

>"User has engaged in [value] conversations with an average length of approximately 47 messages. User poses an average of 1.21 questions per message.
>User's interactions are mostly positive, with occasional constructive feedback and error reporting. User frequently asks 'What', 'How', 'Do', and 'Is' type questions and prefers detailed and comprehensive answers.
>User's average question length is around [value] words, indicating in-depth inquiries.
>User's interaction topics include development, AI discussions, linguistics, data operations, personal interactions, and scripting."

## CONCLUSION:

This guide serves as a comprehensive resource for anyone interested in elevating their interactions with ChatGPT through data distillation. By following the steps outlined, you not only personalize your experience but also engage in a fun, interactive experiment to tailor an AI assistant to your individual needs without fine-tuning the model.

Remember, this process is iterative and sequential, and may require some trial and error based upon the specific responses provided by the assistant. However, the result— a more intuitive and responsive conversational agent— is well worth the effort. Whether you are a beginner curious about the potentials of AI or an expert looking to turbo-charge your prompting capabilities, this guide offers a flexible, explorative approach to get yourself going.  For those keen on delving deeper, the door to advanced data analysis and linguistic theory is now open, and the possibilities are endless.

For my next technique, I’ll be writing up a helpful approach for easy, actionable image prompting with DALL-E 3.

I will do my best to answer any questions and help out others when I can. Feel free to let me know what you think! I appreciate any and all feedback! 

<details>
  <summary><h2>VOCABULARY TERMS / FURTHER READING </h2></summary>
  
  1. #### Interrogative Clause: https://en.wikipedia.org/wiki/Interrogative
  2. #### LDA (Latent Dirichlet Allocation): https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation
  3. #### Sentiment Analysis: https://en.wikipedia.org/wiki/Sentiment_analysis
  4. #### N-gram: https://en.wikipedia.org/wiki/N-gram
  
</details>

## TROUBLESHOOTING:

### TBD
