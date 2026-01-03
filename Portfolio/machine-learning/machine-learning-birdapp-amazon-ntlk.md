---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-birdapp-amazon-ntlk/
---

# Natural Language Processing on Amazon Bird App Reviews

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Classification techniques applied to the 
<a href="https://raw.githubusercontent.com/pycaret/pycaret/master/datasets/amazon.csv" target="_blank">
Amazon Bird App Reviews Dataset
</a> to extract patterns and insights. Key take-outs are:
</p>
<ul>
  <li>a</li>
  <li>b</li>
  <li>c</li>
</ul>

</div>

## Data
The [Amazon Bird App Reviews Dataset](https://raw.githubusercontent.com/pycaret/pycaret/master/datasets/amazon.csv) contains customer reviews of Angry Bird App. The dataset includes 20,000 reviews with the following 2 columns:

1. **reviewText** – The text of the review  
2. **Positive** – Binary label indicating if the review is positive (1) or negative (0)

## Pre-processing
The following pre-processing steps were applied using NLTK:
1. **Tokenization** – Splitting the text into individual words or tokens.
2. **Lowercasing** – Converting all text to lowercase for consistency.
3. **Expand Contractions** – Expanding shortened forms (e.g., "don't" to "do not").
4. **Stopword Removal** – Eliminating common words (e.g., "the", "is") that do not contribute much to meaning.
5. **Punctuation Removal** – Stripping out punctuation marks to focus on words.
6. **Lemmatization** – Reducing words to their base or root form (e.g., "running" becomes "run").

Here is an example of the pre-processed text:

Example Review:
[ORIGINAL]    : This is a one of the best apps acording to a bunch of people and I agree it has bombs eggs pigs TNT 
[LOWERED]     : this is a one of the best apps acording to a bunch of people and i agree it has bombs eggs pigs tnt 
[CONTRACTIONS]: this is a one of the best apps acording to a bunch of people and i agree it has bombs eggs pigs tnt 
[STOPWORDED]  : one best apps acording bunch people agree bombs eggs pigs tnt king pigs realustic stuff
[UNPUNCTUATED]: one best apps acording bunch people agree bombs eggs pigs tnt king pigs realustic stuff
[LEMMATIZED]  : one best apps acording bunch people agree bomb egg pig tnt king pig realustic stuff

Example Review:
[ORIGINAL]    : This is a very entertaining game!  You don't have to be smart to play it.  I guess that's why I like
[LOWERED]     : this is a very entertaining game!  you don't have to be smart to play it.  i guess that's why i like
[CONTRACTIONS]: this is a very entertaining game!  you do not have to be smart to play it.  i guess that is why i li
[STOPWORDED]  : entertaining game ! smart play . guess like ... easy fun games suppose . warned : game highly addict
[UNPUNCTUATED]: entertaining game  smart play  guess like  easy fun games suppose  warned  game highly addictive 
[LEMMATIZED]  : entertaining game smart play guess like easy fun game suppose warned game highly addictive


## Analysis

### Natural Language Processing Techniques
These methods are used:
1. **XX** – aa.  
2. **XX2** – bb.  


### Results

## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/birdapp-amazon-ntlk/machine-learning-birdapp-amazon-ntlk.md)

[← Back to Machine Learning](/machine-learning/)