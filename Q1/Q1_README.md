Learning Basics : 

Understanding how Transformers, Encoders, Decoders and NLP algorithms work : 

A transformer consists of multiple layers of Attention blocks and Feed-forward blocks or Multiple layer perceptrons which process the data which we recieve. The process starts with tokenization, when we receive a sentence and we want to predict the next word in the sentence, we tokenize the sentence into smaller tokens (not neccesarily words) so that we can use them to make sense. After converting them to tokens, the tokens are converted from words to vectors build up from different numbers. This process is known as Embedding, we get embedded vectors after this process. These Embedded vectors are of very high dimensions, the GPT-3 model consisted of vectors in 12808 dimensions. These vectors are run through multiple layers to Attention blocks and MLP blocks. 

Role of Attention block : The attention block is an upgrade to the Word2Vector algorithm and the backbone of modern NLP. The role of Attention is to use previous words in the statement to understand the context of the statement. It uses the current vectors to modify the vectors based on the context. This is done multiple times. Each attention block uses Query, Key and Value matrices to compute the context based meaning of the word. 

The formula used by attention is Z = softmax(K^T . Q / sqrt(dk)) * V

The softmax funtion is a simple way of converting the matrix which has different values ranging from -infi to +infi into values between 0 and 1 and making the sum of all values equal to 1. 

Role of MLP block : The MLP block is a neural network which maps all the neurons from the vector and runs them through the neural network to identify and modify the vectors. The MLP block transverse each token parallely with a linear matrix, a simple ReLU function and another linear matrix. We use the final vector in the tokens and apply softmax to it to get the weighted probabilities of different possible words in the next place. 

Intuition : In a high dimensional space we can imagine that each direction denotes different attribute like gender, height or literally anything. In this space, similar meaning words will have similar directions, i.e. their scalar product will be highly positive and the opposite meaning words will have negative scalar products. So we can map similar meaning words together and make sense of them. 

Resource used  : https://youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&si=pDW8mDsZIaifo1Ks

Understanding BERT : 

BERT is based on a series on encoders which take in the tokens from the statement and run them through multiple encoders. 
It uses Bi-directional format, thus reading the tokens from both directions deepening the understanding of the statement's context. It has been trained on two types of tasks : Masked language modeling and Next sentence prediction.

Input Format:

[CLS] token at the start (used for classification)
[SEP] token to separate two sentences
Token Embeddings + Segment Embeddings + Positional Embeddings

Resource used : https://jalammar.github.io/illustrated-bert/

Understanding basics like stop-words, tokenization, lemmatization, etc. Resource used : https://www.datacamp.com/tutorial/text-analytics-beginners-nltk

