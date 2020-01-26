# boolean-query-retrieval
In this project we will be building boolean query retrieval model using 20_newsgroups dataset

### Requirements
+ python 3
+ nltk
+ pickle

### Pre-processing
+ Removal of meta data in each file
+ Removal of symbols like [!@#$%^&*()] from the tokens
+ Removal of non alpha numeric tokens
+ Lemmatization of tokens
+ Removal of words that are less than size 2 (useless words)

### Methodology 
+ Download the 20_newsgroups dataset which is freely available and place in data folder
+ For each file pre process the file and construct the index dictionary
+ index dictionary will be: { token : list of files containing the token }
+ Following precedence is assumed : NOT > AND > OR
+ Sample User queries :
  - email AND version
  - email OR version
  - NOT email
  - email AND NOT version
  - email OR NOT version
  - email AND version OR print
  - email AND version AND ----OR --NOT--
+ Retrieves all the files that satisfies the above conditions

### Optimisations:
+ When there are NOT followed by NOT, two NOT operations are cancelled each other without calculating again and again
  - NOT NOT boy = boy
+ if query contains only AND operations then, operations are performed in the orderof tokens having minimum postings list.

### References :

+ Followed chris manning text book for making this model. [link](https://nlp.stanford.edu/IR-book/pdf/01bool.pdf)
