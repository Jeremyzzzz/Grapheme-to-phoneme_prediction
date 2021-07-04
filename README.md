# Grapheme-to-phoneme_prediction(half-day coding challenge solution)

**Task**: G2P task on low resource languages such as Slovenian(slv), Adyghe(ady) and Romanian(rum).

**Our Soultion: seq-to-seq biLSTM with attention and character-level embedding on each low resource language.**

**Final Score: Average WER: 37.00, Average PER: 9.39**

**Description**: Grapheme-to-phoneme prediction (G2P) is the task of reading in a written word, and producing its pronunciation in a standardized format (typically, using the International Phonetic Alphabet, or IPA)

For example, a G2P system reading in the word "anemone" should output the sequence /ənɛməni/ (depending on how *broad* the transcription is, we might indicate other linguistic features, such as stress: /əˈnɛməni/, syllabification: /əˈnɛm.ə.ni/, or other important variations in the pronunciation, such as whether a letter is aspirated: /t/ vs /tʰ/, rounded: /r/ vs /rʷ/, palatalised: /p/ vs /pʲ/, or other important pronunciation differences (see https://en.wikipedia.org/wiki/International_Phonetic_Alphabet (Links to an external site.) for the complete IPA).

G2P is often an important step in text-to-speech - text is converted to phonemes, which are then converted to sound waves.  Likewise, automatic captioning systems often do the task in reverse - sound is converted to phonemic representations, and then transcribed.  As with many NLP tasks, G2P is often performed by training deep-learning models on significant amounts of text.

**Evluation**: There are 2 metrics used for calculating the accuracy of a G2P system: Word Error Rate (WER), and Phoneme Error Rate (PER).  WER is simply the percentage of words that the model fails to predict correctly; PER give "partial credit" when you get most of a word correct: producing /ænɛməni/ would give you 1.00 WER (higher is worse), but 0.14 PER. Provided scripts(`evaluate.py, evalib.py` can be used for evaluation) 

**Scoreboard:**

||ady|slv|rum|
----|---|---|---
dev_wer |44.00|64.00|12.00|
dev_per |11.13|16.23|2.70|
test_wer|N/A|N/A|N/A|
test_per|N/A|N/A|N/A|


## Pipeline of task

### 1. Data exploration
  - size of each split
  - vocabulary

### 2. Preprocessing(TorchText)
  - tokenization
  - build vocabulary
  - bucket iterator

### 3. Model architexture(seq2seq+attention)
  - Encoder(bidirectional)
  - Decoder
  - Character-level embedding
  - Attention(concat product)

### 4. Evaluation(evaluate.py)

### 5. Prediction

## Future work

### Early stopping with more epochs
### Hyperparameter Tunning
### Transfer Learning with high-resource languages
### ...


Source: UBC master of data science in Computational Linguistics capstone coding challenge
