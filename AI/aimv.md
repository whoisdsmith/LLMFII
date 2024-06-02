---
aliases:
  - AIMV
tags:
  - music
  - speech-recognition
  - instrument-classification
---
# AIMV
AI model that generates a Music Video from a .wav file, using Instrument Classification, Speech Transcription, and Video Generation. 
## *Architecture*:
### Content Transcription
  - #### Find Datasets
    - [Ismir](https://www.ismir.net/resources/datasets/)
  - #### **Instrument Classification**
    - [Musical Instrument Identification](https://www.mdpi.com/1424-8220/22/8/3033/pdf?version=1650009477)
    
    - [Drum Sound Subtype Classification](https://www.researchgate.net/publication/41538774_Classification_of_snare_drum_sounds_using_neural_networks)
    
    - [Timbre Identification](https://iopscience.iop.org/article/10.1088/1742-6596/1856/1/012006/pdf)
    
    - [Sound Event Detection](https://arxiv.org/pdf/2107.05463)
    
    - [Medley-solos-DB: a cross-collection dataset for musical instrument recognition](https://zenodo.org/record/2582103)
    
  - #### Speech Recognition (is speech present?) and subsequent Speech Transcription (if present) using OpenAI Whisper ASR. use --language Spanish if Spanish, etc
    [Whisper](https://github.com/openai/whisper) uses Transformer Neural Networks
    
  - #### Concatenation of the above into a general content transcription
    For an audio window of length 1 second containing a Vocal saying loudly "Heart" over a crash cymbal hit:
      - Return (loud, heart, crash, splash, synth, hexcolorvalue)
 
    This translates to:
      -   Volume relative to the running average volume + Vocal transcription + 3 most confident instrument identifications + color name (from frequency->hex map)
      -   Each of the three identifications need to meet a confidence criteria, say 70%, to make the list. Ex: (crash, rimshot, snare) 
      - if less than 3 instruments identified with 70% confidence, i.e. list is (crash), fill the list with the second-and-third most confident guess for those that have been identified with confidence, in the case of crash it could have been a splash instead or a weirdly textured synth. (crash, splash, synth).    
      - Ex. with 70% confidence, (guitar, vocal) -> (guitar, vocal, bass), bc the "guitar" guess has a 2nd-most-confident guess of "bass"
  
    We then port this to a sentence. 
    
      - Volume informs the intensity of the image, ie if loud/quiet vocal saying Heart, say "person screaming/yelling/whispering, action + object.
     
      - Action being looking at, running at, holding, etc, the object in question ("heart"). Choose action randomly. 
    
      - Further abstract the crash, splash, drum (transient description) by mapping these to additional, more abstracted related words. 
        - Text similiarity with Gensim [link](https://betterprogramming.pub/introduction-to-gensim-calculating-text-similarity-9e8b55de342d)
 
        - (crash, splash, synth) -> (impact, wave, tech)
        - (kick, bass, tom) -> (canon, deep, bounce)
        - (cello, vocal, guitar) -> (floating, vibrate, pedal)
        - add these abstracted words to the final text description

      - Category (drum, guitar, violin, vocal, piano, bass) given by the initial transient description determines the verb (hits, picks, plays, sings, plays, plays)
        - If Drum category and not Kick, assign "Drum stick strikes" as the verb
      - Least likely category gets assigned to the beginning of the metaphorical/abstraction section, with the last element of the abstraction as adjective before it.
      - If speech present, assign a "loudly" or "softly" according to volume of the speech
      - t = transients, a = abstractions
      - (ifspeech)"Person(volume) sings, (action) a (transciption), in the background to a (t1, t2) (verb), with a foreground (a3)(t3)(a2)(a1), the scene has a (hexcolorname) color palette."

    #### Examples:
      - (loud, heart, crash, splash, synth, hexcolorvalue, impact, wave, tech) -> "Person loudly sings, holding a heart, alongside a Crash and Splash hit with a foreground techy synth wave impact, the scene has a (hexcolorname) color palette."
        - Abstraction is the foreground, if speech is present, it is "alongside" the background of the instruments. 
      - (loud, N/A, kick, bass, tom, hexcolorvalue, canon, deep, bounce) -> "Kick hits and Bass plays in the background. In the foreground a bouncey tom deep canon, the scene has a (hexcolorname) color palette"
      - (quiet, N/A, cello, vocal, guitar, hexcolorvalue, floating, vibrate, pedal) -> "Cello plays and Vocal sings in the background. In the foreground a pedaly guitar vibrate floating, the scene has a (hexcolorname) color palette."  
        - Vocal identified as an instrument present, but no intelligible speech was transcribed. Likely a "hmmmmm" or an "oooooooo" or similar.

### **Video Generation**
  - [CogVideo](https://github.com/THUDM/CogVideo) uses Transformer Neural Networks
  - [CogVideoPaper](https://github.com/THUDM/CogVideo)
