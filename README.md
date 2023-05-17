# NLP-code-sample 

This is a wrap up work sample from the project in Wharton Analytic Fellowship program to understand customer complaints through Natrual Language Processing (NLP) models. Due to the data agreement, the result are not allowed to show.

## Sentiment Analysis 

determine whether the customer comment is positive, negative or
neutral by assignment sentiment scores to the topics, categories or
phrases.

### Valence Aware Dictionary and Sentiment Reasonor 

- Lexicon-based model
- Pros: Contextual elements, like punctuation and degrees are taken into account; able to customize the sentiment threshold
- Cons: Poor at complex sentence such as sarcasm or memes; poor at dealing with misspellings and grammatical mistakes


 
## Keyword Extraction

Keyword extraction is a technique used to automatically
extract the most relevant words and phrases from text to
help summarize the content.

### Bidirectional Encoder Representations from Transformers (BERT)

   - Pros: effective with complex document; creates word and document enbeddings; words most similar to the entire document are extracted.
   - Cons: Computationally expensive; may require retuning for different tasks.
    
**Input**: pass each customer comment into the keyword extraction pipeline
   
**BERT encoder**: take the comment and break it into the n-grams and words that could be keywords. Then BERT encodes both the entire comment and all candidates as vectors.
   
**Candidate Ranking**: Candidates are selected based on 
  1. relevance score: how similar candidate vectors are to the vector of the entire document; 
  2. Diversity score: how the selected keywords are different from each other.
   
   
## Topic Modeling

Scans through documents, examines how words and phrases co-occur, and learns clusters of words that best characterize these document

### Latent Dirichlet Allocation (LDA)

Assume probability distribution and using an iterative process to update best topic. By running through multiple iterations and large text corpus, we are optimizing over the allocation of topics on each document and the composition of words for each topic.

- Pros: takes into account bigrams (words that appear close together)
- Cons: Requires lots of data due to high variance; lack interpretability; more inaccurate to short texts


