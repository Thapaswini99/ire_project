# Extraction and summarization of tweets

<b>Why automation of summarization?</b>
<br/>
With the rise of microblogging mainly Twitter in recent years, automated tweet summarization is attracting people as it helps them to get the main views in a short amount of time efficiently.

## Our Approach
### Approach 1
- we used a document-level reconstruction framework named DocRebuild, which reconstructs the documents with summary
  sentences through a neural document model and selects summary sentences to minimize the reconstruction error. 
  We used beam search for selecting the selecting the summary sentences.
### Approach 2
- Our second model is based on the pagerank algorithm which is used generally for ranking the webpages. Here we use the same   algorithm for ranking the most important tweets. 
  
Our code can be found [here](https://github.com/priyendumori/Extraction-and-Summarization-of-Tweets).

### Dataset Preprocessing 
To use the tweets, we had to clean them:
- remove '\#' from hashtags, punctuation and special characters, links and convert all text to lowercase.  
- changing abbrevations to full forms


### Models and results
We trained Doc2vec model on our twitter corpus and some documents corpus and later used the model to obtain paragraph vectors.The tweets are ranked separately by their cosine similarity to the centroid vector, in decreasing order.he N best tweets are selected as a Candidate set from which the K most appropriate tweets are selected to form a summary. The K most important tweets are selected by using an algorithm called beam search,


Following are the results for some of the hashtags :

<br/>
<b> globalwarming </b>
- model1
  Is to blame for When you see trends... it becomes undeniably linked to global change. 
  confirmed by planet Earth 'skin temperature test' The last years and century statistics are the real confirmation 
  michh_31415 and often need lots of computing power, which is a problem in view of and Here is a nice position paper by       allen_ai to raise awareness for these issues 
  The decline in sea ice seen in the Arctic in recent decades has been linked by scientists to the spread of a deadly virus n   in marine mammals 
  Did you know that glass can be recycled and re-manufactured an infinite amount of times 

- model2
  michh_31415 and often need lots of computing power, which is a problem in view of and Here is a nice position paper by       allen_ai to raise awareness for these issues
  Walking my son to school last week, wondering at the leaves on the ground, it hit me that I was witnessing remains of the     that worked for millions of years and possibly the source of today's hydrocarbons.
  The reason all governments of Australia wont take seriously the threat of global warming is because they are too scared to   be known for doing something about it.
  Our summer was cooler than average as well, sad the movement used to push the agenda!
  Because of Global Warming, record wildfires everywhere nowdays have become the new norm Australia, California, Sweden.. my   heart goes out to all the poor animals trapped or worse

#### Structured Self-Attentive Sentence Embedding
We used a model for extracting an interpretable sentence embedding by using self-attention. Instead of using a vector, we use a 2-D matrix to represent the embedding.

Following are the evaluation metrics:
+ Accuracy : 0.885
+ Precision : 0.885
+ Recall : 0.885
+ F1 Score : 0.885

#### LSTM Models
Simple LSTM model in principle does capture the structure of the sentence, but does not incorporate the structural dependencies presnet in the sentence explicitely. 
We also have implemented a Child-Sum Tree-LSTM model on the dependency tree of the sentence, which is better than the Simple LSTM model at preserving semantic information as it incorporates information from multiple child units.
Following are the evaluation metrics :

<br/>
<b> Simple LSTM Model </b>
+ Accuracy : 0.874
+ Precision : 0.861
+ Recall : 0.861
+ F1 Score : 0.861

<b> Tree LSTM Model </b>
+ Accuracy : 0.920
+ Precision : 0.920
+ Recall : 0.920
+ F1 Score : 0.920

## Conclusion
Tree-LSTM model gave the best results.
