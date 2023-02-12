# Detecting Depression on Twitter


## Project Overview
___
Twitter posts can be a valuable source to find clues that hint to the presence of mental illness among individuals. To take advantage of this, my project seeks to analyze recent twitter posts and natural language processing to predict the emergence of depression - one of the most prevalent mental illnesses. To identify a tweet indicating clinical depression, nine different models are employed, with each having a different classification algorithm and word embedding. We find that the model with the highest accuracy and precision scores is the Neural Net with 3 hidden layers and Keras embedding, while the SVM with GloVe embedding performed the worst. Furthermore, this analysis is complimented with a sentiment and emoji analysis. We find that tweets indicating depression have a more negative sentiment. Additionally, emojis such as the crying face, skull, face with tear, holding back tear, etc are more prevalent among tweets indicating depression. 

### Data and Methods
___
The data for predictive modeling includes 2,934 twitter posts from 2/8/2023 collected through the Twitter API, with exactly half being classified as depressed, and the other half deemed not depressed. Those that indicate depression are obtained by entering into the query relevant keywords closely associated with depressed behavior, such as “depression”, “antidepressants”, “anxiety”, etc. I then manually remove any tweets that that use these keywords casually and don't have enough information to show that the user is depressed. I also remove tweets that use them to describe negative emotional experience, but is not an official diagnosis (i.e. hair depression, post-concert depression, etc). Finally, I remove depressed keywords during the tokenization process to reduce overfitting. The tweets not indicating depression on the other hand, contains normal content and is filtered to exclude any data that indicates depression by omitting tweets that contain the same keywords aforementioned. To increase noise, I include some of the tweets that use the depressed keywords casually.

These data are then fed into nine machine learning models, all of which are fine tuned and use various word embedding techniques. Namely, we focus on the following approaches: logistic, support vector machine, and neural networks. For the word embedding, we apply the bag of words, TF-IDF, and GloVe techniques on the logistic and support vector models. For the neural networks, we use the Keras embedder and BERT. To determine model performance, I analyze accuracy, precision, and recall, but pay most of the attention towards precision

The project also considers sentiment, the use of emojis, and word frequency.
The sentiment analysis compares the distribution of the Vader composite scores between depressed and not depressed tweets. To analyze the emojis used in depressed tweets, I also collected xxx tweets that containing emojis from 2/11/2023, with each tweet also assigned to the binary classification of indicating depressed or not.  This data is then used to compare the top 15 most popular emojis used between depressed and normal tweets. Finally, I display the top 15 most significant features (in terms of word frequency), as well as the 15 least significant. 

### Results
___
The sentiment analysis results show that while both depressed and not depressed both have a relatively similar positive Vader score, those that are indicative of depression have a much stronger negative score and a composite score that is more negative than positive.  

The emoji analysis finds that the depressed tweets are more closely associated with the crying face, upside down face, melting face, weary face, and pensive face, whereas the  normal tweets are more closely tied to the blue diamond, fire sign, heart hands, and smiling face with hearts.

We also find that the Neural Network, with 3 hidden and 1 dropout layer has the best performance for precision with 91% accuracy, followed by the single hidden layer neural network.

The results from all models are as follows:

* Neural Net (3 Hidden Layers) - Keras: 91%
* Neural Net - Keras: 89%
* Logistic - TF-IDF: 80%
* Neural Net - BERT: 80%
* SVM - TF-IDF: 78%
* SVM - Bag of Words: 76%
* Logistic - Bag of Words: 74%
* Logistic - GloVe: 55%
* SVM - GloVe: 55%

### Limitations
___
Despite the methods used to deal with any complications, there are also some limitations of the study that should be acknowledged for future studies to consider. First, most research using social media data runs into the issue of sarcasm. While this research does not come across this issue very severely, even before manually removing irrelevant tweets from the data, it is still difficult to recognize tweets that appear genuine without understanding the the author of the post themselves. Additionally, this study is primarily focused on diagnosis of depressive disorder rather than other prevalent mental illnesses, such as anxiety disorder, even when we include ‘anxiety’ as part of our keywords list. Lastly, only five keywords are used to identify tweets from depressed users. Thus, we encourage future researchers to include a wider scope of keywords to include a broader range of tweets hinting to depression in terms of context, such as hopeless, sad, lonely, suicide, etc. 
