# Detecting Depression on Twitter


## Project Overview
___
Twitter posts can be a valuable source to find clues that hint to the presence of mental illness among individuals. To take advantage of this, my project seeks to analyze recent twitter posts and natural language processing to predict the emergence of depression - one of the most prevalent mental illnesses. To identify a tweet indicating clinical depression, nine different models are employed, with each having a different classification algorithm and word embedding. We find that the model with the highest accuracy and precision scores is the Neural Net with 3 hidden layers and Keras embedding, while the SVM with GloVe embedding performed the worst. Furthermore, this analysis is complimented with a sentiment and emoji analysis. We find that tweets indicating depression have a more negative sentiment. Additionally, emojis such as the crying face, skull, face with tear, holding back tear, etc are more prevalent among tweets indicating depression. 

### Data
___
The data for predictive modeling includes 2,934 twitter posts from 2/8/2023 collected through the Twitter API, with exactly half being classified as depressed, and the other half deemed not depressed. Those that indicate depression are obtained by entering into the query relevant keywords closely associated with depressed behavior, such as “depression”, “antidepressants”, “anxiety”, etc. I then manually remove any tweets that that use these keywords casually and don't have enough information to show that the user is depressed. I also remove tweets that use them to describe negative emotional experience, but is not an official diagnosis (i.e. hair depression, post-concert depression, etc). Finally, I remove depressed keywords during the tokenization process to reduce overfitting. The tweets not indicating depression on the other hand, contains normal content and is filtered to exclude any data that indicates depression by omitting tweets that contain the same keywords aforementioned. To increase noise, I include some of the tweets that use the depressed keywords casually.


### Methods
___

These data are then split into training and testing data using a stratified technique. The training data are used to train nine machine learning models, all of which are fine tuned with GridSearch CV and use various word embedding techniques. Namely, we focus on the following approaches: logistic, support vector machine, and deep neural networks. For the word embedding, we apply the bag of words, TF-IDF, and GloVe techniques on the logistic and support vector models. For the deep learning portion, we use the Keras embedder and BERT. The models then generate predictions on the validation data. To determine model performance, I analyze accuracy, precision, and recall, but pay most of the attention towards precision, as it is important that the model does not incorrectly classify depressed tweets as not depressed.

The project also considers sentiment, the use of emojis, and feature significance.
The sentiment analysis compares the distribution of the Vader composite scores between depressed and not depressed tweets. To analyze the emojis used in depressed tweets, I also collected xxx tweets that containing emojis from 2/11/2023, with each tweet also assigned to the binary classification of indicating depressed or not.  This data is then used to compare the top 15 most popular emojis used between depressed and normal tweets. Finally, I display the top 15 most significant features (in terms of word frequency), as well as the 15 least significant. 

### Results
___
The sentiment analysis results show that while both depressed and not depressed both have a relatively similar positive Vader score, those that are indicative of depression have a much stronger negative score and a composite score that is more negative than positive.  

The emoji analysis finds that the depressed tweets are more closely associated with the crying face, upside down face, melting face, weary face, and pensive face, whereas the  normal tweets are more closely tied to the blue diamond, fire sign, heart hands, and smiling face with hearts.

The most strongly associated features of depression among Twitter users are related to taking medicine, negative emotions, time words, and certain actions such as work, whereas the least significant features are collectively more miscellaneous.

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

Despite the methods used to deal with any complications, there are also some limitations of the study that can create new avenues for future researchers to consider. First, most research using social media data runs into the issue of sarcasm. While this research does not come across this issue very severely, even before manually removing irrelevant tweets from the data, it is still difficult to recognize tweets that appear genuine without understanding the the author of the post themselves. Second, this study is primarily focused on the pretense of depression rather than other prevalent mental illnesses, such as anxiety disorder, even when we include ‘anxiety’ as part of our keywords list. Fourth, this study employs several word embedding techniques, but does not consider bigrams or other ngrams that could be important to study. Fifth, this binary classification approach does not take into account the severity of the depression within tweets classified as depressed. In the future, researchers could consider producing a larger scale to show the different levels of depression. Finally, only five keywords are used to identify tweets from depressed users. Additionally, only five keywords are used to identify tweets from depressed users. Thus, we encourage future researchers to include a wider scope of keywords to include a broader range of tweets hinting to depression in terms of context, such as hopeless, sad, lonely, suicide, etc. Finally, our models using the GloVe embedder show poor performance, even compared to the outdated bag of words or the TF IDF approaches. While GloVe usually tends to have better performance than other word embedding techniques, GloVe it is quite possible that the data used does not have enough observations to show the true potential of GloVe.
