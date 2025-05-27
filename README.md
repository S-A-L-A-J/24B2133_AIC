AI Community Assignment
-
For each question, below are the setup steps for local excecution, basic explanation of the problem, my analysis, experiments and comments, all the links to resources used. Before starting, i would like to mention that i had worked with MLP and CNN earlier so i had experience in the question 2 but for question 1 and 3, I had to read up on the internet and understand what their respective topics did, so both of those questions contain a readme file explaining what i collected from the resources and what my understandings were. 

Question 1 
-
Steps for local excecution : Use the requirements.txt file to install all the required libraries for the question. Once you download the github repo, you should be directly able to run the jupyter notebook by running all. Note : for this i have used python 3.10.16 in my venv. I have also mentioned a check for GPU support.

Explanation of the question : The train.csv file contains a lot of statements, each with a label of the sector or topic of study to which it is related to. Using preprocessing by stop word removal, punctuation elimination and lemmatization. We also converted the labels to the data into encoded format so it is easy for us to access them. Tokenizing the sentences and return tensors with the sentence present in a tensor. Then i used the BERT base-uncased model to embedd my tokenized sentence into vectors. Based on this model, the vectors to each type of sector is placed in a high dimensional space. Using this dataset, the model is trained, i.e. the model can predict when any random sentence given based on its semantics, that the given sentence is belonging to which class. At the end of the program, i have tried a random statement. 

Resource used : 
3Blue1Brown videos - https://youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&si=pDW8mDsZIaifo1Ks
JayAlammar paper on BERT - https://jalammar.github.io/illustrated-bert/
DataCamp website for basics of NLP - https://www.datacamp.com/tutorial/text-analytics-beginners-nltk

A few things that i inferred from this question :
1. The preprocessing of data is very important, it prevents the model from focusing on words that don't add meaning or might take the model off-track. Also, the algorithm i used didn't remove numbers but i feel that numbers being used for NLP won't be useful sometimes when the data means something else, so that is something i wasn't sure about.
2. Tokenization of the sentence using the bert base-uncased model without specifying the max length for the tokenization sometimes make the model train for a lot longer, i used a GPU to train my model but without using any max length defined, it took more than 4-5 hours to even close to completing the training. So i had to add the max length to be 128, then too it took around 3 hours to train the model on a gpu. Hence trainng and building these models from scratch take a lot of computational power and building an attention mechanism and mlp transformer block from scratch would be very difficult for my computer. Using the bert model was better.
3. The accuracy of the model is good, hence most of the predictions are correct. The precision and recall of the model are in a decent range indicating that the model avoids false positives well and detects most positives, the validation loss is mildly high suggesting that there might be some overfitting. Overall, the F1 score of the model is balanced indicating that both the false positives and negatives are well managed.
4. The model isn't quite perfect yet, some random sentences which i input at the end for testing the model were given some different labels than expected. The reason for this might be that the vectors present in the high-dimensional space might be in close proximity for some cases, so to prevent this we might try to decrease the threshold for accepting the query to be matched. Another possible reason that i can think of is that some queries which i add might not have some embeddings exactly close to those of the existing labels, so they might find the nearest and output them.



Question 2
-
Steps for local excecution : Import the repo and all the test train files have been kept with the ipynb file, and all paths are set. Just run the notebook and check the results.

Explanation of the question : Using a pretrained CNN model, by freezing its lower layers and then adapting a new Linear layer for converting the output to our usage that was to classify given images into 10 classes of fashion clothing. Then once overlaying our layer on top of the pretrained CNN, unfreeze the layers to get the best of the model. This method of using a pretrained model becuase we cannot train a model on a very large data ourselves due to limited computation power is known as transfer learning. For my implementation i used the ResNet50 model. 

Resources Used : Patrick Loeber's series on PyTorch -  https://youtube.com/playlist?list=PLqnslRFeH2UrcDBWF5mfPGpqQDSta6VK4&si=ob2COI27kHo4Z-6J

Insights and errors : 
1. I had not previously worked with Ubyte files, instead i imported it directly from torchvision or keras datasets. So i learnt how to use Ubyte files with help of CHatgpt and implemented it into my program.
2. The accuracy for my model even after unfreezing the bottom layers was still decent but it could have been much better, it might be achieved by increasing the number of layers or the neurons per each layer
3. Since we are identifying clothes and fashion accessories, it is better to have more neurons per layer so that many different features for each type of clothing can be understood by the model and find them.


Question 3
-
Steps for local excecution : Add any PDF into the folder and change the path in the ipynb file to use the PDF. By default, i have used a SOM101 module as the pdf and tested the model on that. 

Explanation of question : I have described the question and the theory behind it in the a theory md file in the Q3 folder in very detail.

1. I tried two different ways for semantic chunking, first i tried to create chunks of roughly 300 words or tokens assuming that most of the semantics would be covered in it but there was a chance of error. So instead i used a basic separation using paragraphs, because generally in any pdf the author has separated the content into paragraphs for clear outline between different topics. So for once i divided the chunks on basis of paragraphs, then i applied semantic chunking, i.e. embedding each chunk with a vector and then on the basis of very closesly placed vectors for different chunks, we merged those chunks to get semantically merged chunks.
2. We can use more than 3 nearest neighbours for the query, but it is generally okay to use only 3 because in all the testings i did, using top 3 almost always gave the perfect answer based on the context of the pdf.
3. The groq api used many of the exact words from the pdf as it is which might suggest that the groq api uses more of the content directly from the pdf rather than using its LLM feature to predict and develop follow up text.
4. I didn't know exactly how the groq api works so i had to use some external help to understand how to prompt must be sent to the api key. 
