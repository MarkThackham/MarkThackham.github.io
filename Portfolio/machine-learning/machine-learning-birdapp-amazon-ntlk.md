---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-birdapp-amazon-ntlk/
---

# Natural Language Processing on Angry Bird App Reviews

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Natural language processing techniques applied to the 
<a href="https://raw.githubusercontent.com/pycaret/pycaret/master/datasets/amazon.csv" target="_blank">
Bird App Reviews Dataset
</a> to extract patterns and insights. Key take-outs are:
</p>
<ul>
  <li><strong>Text cleaning is essential</strong> → NLTK preprocessing (tokenisation, lowercasing, contraction expansion, stopword/punctuation removal, lemmatisation) standardises messy review text and improves signal for downstream NLP.</li>
  <li><strong>VADER gives a strong baseline</strong> → Rule-based sentiment scoring using the compound score separates positive vs negative reviews well (<strong>AUC ≈ 0.83</strong>), showing you can get good performance without a complex model.</li>
  <li><strong>Language differs clearly by sentiment</strong> → Bigram word clouds highlight distinct phrasing in positive vs negative reviews, making key themes and tone differences visible at a glance.</li>
  <li><strong>Feature methods surface different insights</strong> → Frequency-based “importance” tends to elevate short/common phrasing, TF-IDF highlights distinctive/issue-heavy reviews, and LDA coherence suggests the corpus is best summarised with <strong>2 main topics</strong>.</li>
</ul>

</div>

## Data
The [Bird App Reviews Dataset](https://raw.githubusercontent.com/pycaret/pycaret/master/datasets/amazon.csv) contains customer reviews of Angry Bird App on the Amazon Kindle Fire. The dataset includes 20,000 reviews with the following 2 columns:

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
```text
[ORIGINAL]    : This is a one of the best apps acording to a bunch of people and I agree it has bombs eggs pigs TNT king pigs and realustic stuff
[LOWERED]     : this is a one of the best apps acording to a bunch of people and i agree it has bombs eggs pigs tnt king pigs and realustic stuff
[CONTRACTIONS]: this is a one of the best apps acording to a bunch of people and i agree it has bombs eggs pigs tnt king pigs and realustic stuff
[STOPWORDED]  : one best apps acording bunch people agree bombs eggs pigs tnt king pigs realustic stuff
[UNPUNCTUATED]: one best apps acording bunch people agree bombs eggs pigs tnt king pigs realustic stuff
[LEMMATIZED]  : one best apps acording bunch people agree bomb egg pig tnt king pig realustic stuff
```

Example Review:
```text
[ORIGINAL]    : This is a very entertaining game!  You don't have to be smart to play it.  I guess that's why I like it...it's easy and fun and that's what games are suppose to be.  Be warned: this game is highly addictive.
[LOWERED]     : this is a very entertaining game!  you don't have to be smart to play it.  i guess that's why i like it...it's easy and fun and that's what games are suppose to be.  be warned: this game is highly addictive.
[CONTRACTIONS]: this is a very entertaining game!  you do not have to be smart to play it.  i guess that is why i like it...it is easy and fun and that is what games are suppose to be.  be warned: this game is highly addictive.
[STOPWORDED]  : entertaining game ! smart play . guess like ... easy fun games suppose . warned : game highly addictive .
[UNPUNCTUATED]: entertaining game  smart play  guess like  easy fun games suppose  warned  game highly addictive 
[LEMMATIZED]  : entertaining game smart play guess like easy fun game suppose warned game highly addictive
```

## Analysis

### Natural Language Processing Techniques
These methods are used:
1. **VADER Sentiment Analysis** – To analyze the sentiment of the reviews, providing scores for positive, negative, neutral, and compound sentiment, often used for social media text. (VADER = Valence Aware Dictionary and sEntiment Reasoner)
2. **Word Cloud** – To visualize the most frequent words in the reviews, helping identify key themes and topics.
3. **Importance Frequency** - Calculate an importance score for each review based on the frequency of words in the review divided by the number of words in the review.
4. **TF-IDF Vectorization** – To convert the text data into numerical format by calculating the Term Frequency-Inverse Document Frequency, which reflects the importance of words in the reviews.
5. **Latent Dirichlet Allocation (LDA)** – To identify topics within the reviews by grouping similar words together based on their co-occurrence patterns.

#### Results - VADER Sentiment Analysis

VADER (Valence Aware Dictionary and sEntiment Reasoner) is rule-based sentiment analysis designed especially for short, informal text like tweets and product reviews. It works by looking up words and phrases in a sentiment lexicon (each term has a built-in positive/negative “valence” score) and then adjusting those scores with heuristics that capture how people actually write online—things like negation (“not good”), intensifiers (“very good”), punctuation and capitalization (“GOOD!!”). It combines these signals into four outputs: positive, negative, neutral, and a single compound score (a normalized overall sentiment from -1 to +1) that’s often used as the main summary.

For this analysis, we focus on the compound score to classify reviews as positive or negative, and evaluate the classification performance which yields and AUC of 82.54%.

##### Most Positive and Negative Reviews

Print 3 most positive reviews:
```text
0.9976 :  good game get it funny funny funny funny fun fun fun fun fun fun fun fun fun fun must have fun fun get app it is fun fun fun get app fun fun gunner than fun fun fun
0.9966 :  Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Cool. Was I suppose to say something else?
0.9928 :  free app free app first commentfree free free free free free free free free free free free free apppppppppppp of the day
```

Print 3 most negative reviews:
```text
-0.9911 :  hairy ball sucks!  will not talk.l hate it ,l hate it ,l hate it ,l hate it ,l hate it ,l hate it ,l hate it ,l hate it ,l hate it ,l hate it
-0.9841 :  Task killers are worse than useless with Android 2 and later. Killing running processes can mess up your phone. Killing idle processes really has no effect on performance. Automatic task killers will always add some load to your CPU, so this really hurts
-0.9805 :  boring boring boring boring boring boring boring boring boring boring boring boring boring boring boring boring I only put 5 stars cause I felt like it
```

#### Results - Word Cloud
A word cloud is a simple text-visualization that shows the most common words (or short phrases) in a dataset, with more frequent terms drawn larger (and often bolder) so themes “pop out” at a glance. To build one, you typically clean and tokenize your text (lowercasing, removing URLs/@mentions/stopwords, optionally stemming/lemmatizing), count term frequencies, then map counts to visual weights (font size) and place words in a layout that avoids overlaps. 

For this analysis, bigrams (two-word combinations) were used to capture more context than single words alone. The word clouds below show the most frequent bigrams in positive and negative reviews. It can be seen there are key differences between the positive and negative reviews.

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/birdapp-amazon-ntlk/bigram_wordcloud_positive.png"
         alt="bigram_wordcloud_positive"
         width="350">
    <figcaption>WWord Cloud - Positive Reviews</figcaption>
  </figure>

  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/birdapp-amazon-ntlk/bigram_wordcloud_negative.png"
         alt="bigram_wordcloud_negative"
         width="350">
    <figcaption>Word Cloud - Negative Reviews</figcaption>
  </figure>
</div>

#### Results - Importance Frequency
This approach assigns an “importance” score for each review using a simple word-frequency heuristic. Using **unigrams** a corpus-wide frequency table shows how often each word appears across all reviews. Then each review is scored by summing the frequencies of its words, normalised by the number of words so longer reviews don’t automatically score higher. The formula is:

\[
\text{scoresNorm}=\frac{\sum_{w \in \text{review}} \text{freq}(w)}{|\text{review}|}
\]

Three most important reviews:
```text
5423.0 :  poor App
5406.0 :  I Love This App. When I am Board I play this game. Love, Love, Love this app. I think you should her this app.
5098.857142857143 :  I play on this app all the time! I love it. I have not had any problems with it! great app
```

Three least important reviews:
```text
1.0 :  Yawn
2.0 :  Bleh
4.96 :  iiiii gfffffff ff hi Fdr hy Gascony. ffggyyg.  vggg guvcdc aback jdndnx aka bdb Japan Jens Kans bus jams iq hsbsbdb hdjcuce nnxk hemmed ksjd
```

#### Results - TF-IDF Vectorization
TF-IDF (Term Frequency–Inverse Document Frequency) is a way to turn text into numbers by scoring each word based on:
- **TF (Term Frequency):** how often a term appears in a document. More occurrences → higher weight.
- **IDF (Inverse Document Frequency):** how rare the term is across the corpus. Terms that appear in many documents get down-weighted.

The formula is:
\[
\text{tfidf\_score}(d)=\sum_{t \in V}\text{tfidf}(t,d)
\quad\text{where}\quad
\text{tfidf}(t,d)=\text{tf}(t,d)\times \log\left(\frac{N}{df(t)}\right)
\]

Three reviews with highest TF-IDF scores:
```text
5.254 :  I'm serious... I download a lota useless apps, but... this one is worse than the worst app in the world, bey. fifb cicvr ric eud ddjdje e such dwid dEric sod d eifhe eididic f ejdjcic. ehfudbr fjfhfhfudhd r r fvfuchr fbfur e r rbfhr. rhfufvr vfhfu f dhcu
5.2319 :  lThe absolute best Bible app for the Kindle Fire paid or free. What really sold me is the &quot;Night Mode&quot; setting. White text on a black background makes reading off a lit screen easy on the eyes. Super slick interface. Navigation is a breeze. Jum
5.2228 :  Crashes on startup with a black screen on Toshiba Thrive (HC 3.2.1, Tegra 2). Eventually music will start playing but the game never displays. Tried it on my Droid (GB 2.3.7, A7@1.2ghz) as well and same thing happened. Bummer, sd the game idea looks inte
```

Three reviews with lowest TF-IDF scores:
```text
0.0 :  not for me
0.0 :  No:(
0.0 :  n o t.  w o r t h. I t.  n o p e.  n o p e.  s o j u s s. k e e p.  g o n .
```

#### Results - Latent Dirichlet Allocation (LDA)
LDA (Latent Dirichlet Allocation) is a topic-modeling method that automatically discovers “topics” in a collection of texts by finding groups of words that frequently appear together. It assumes each document is a mixture of multiple topics, and each topic is a probability distribution over words. Using iterative inference, LDA estimates those hidden topic and document-topic distributions so it can assign topic proportions to every review or tweet. The result is an interpretable set of topics and, for each text, how strongly it relates to each topic.

To determine the number of LDA topics, models are trained across a small range (here, 2–5 topics) and computing a coherence score for each one, which estimates how semantically consistent and interpretable the topics are. The typical choice is the topic count with the highest (or near-highest) coherence—often the “elbow” where gains start to level off—balancing interpretability with model complexity.

The coherence scores for different topic counts are shown in the plot below. The score peaks at 2 topics, which is selected as the optimal number.
<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/birdapp-amazon-ntlk/coherence_score.png"
         alt="Coherence Scores"
         width="350">
    <figcaption>Coherence Scores</figcaption>
  </figure>
</div>

Selecting 2 topics, the top words for each topic along with their probabilities are shown in the bar chart below. This helps interpret what each topic represents based on its most probable words.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/birdapp-amazon-ntlk/topic_words_probabilities.png"
         alt="Topic Words and Probabilities"
         width="350">
    <figcaption>Topic Words and Probabilities</figcaption>
  </figure>
</div>

## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/birdapp-amazon-ntlk/birdapp-amazon-ntlk.ipynb)

[← Back to Portfolio](/machine-learning/)