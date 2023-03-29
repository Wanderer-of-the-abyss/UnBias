# UnBias
UnBias is project whose goal is to create an abstractive summarization model that can generate neutral summaries from politically biased news articles. 

This repo currently by no means represents the final version of the project, this project is currently work in progress, the below is an proposed implementation plan, which has been partially implemented and constantly updated as the project progresses, more updates to come soon :) 

## Data

Most data is to be scraped from [AllSides](https://www.allsides.com/unbiased-balanced-news) as it contains news article from the entire political spectrum, along with a detialed fact based analysis of any particular article, and the data used to train the classifier is availaible in json format from this repo [Article-Bias-Prediction](https://github.com/ramybaly/Article-Bias-Prediction), additionally the [All The News](https://www.kaggle.com/datasets/snapcrack/all-the-news) from kaggle can be used by replacing the news source with their apparent bias score from AllSides. Approximately 100k+ news articles along with thier labelled score are avalaible for training.

## Abstractive Summarization Model:

A pre-trained abstractive summarization model, such as BART or T5, will be fine tuned on the dataset. The model wil generate neutral summaries from politically biased articles. The pre-trained model will be trained on politically biased news articles , along with their neutral summaries. An appropriate loss function like regular cross-entropy loss would be used. An implementation of the fine tuning of the T5 model on a BBC news (political bias: centre) article dataset is done [HERE](https://github.com/Wanderer-of-the-abyss/UnBias/tree/main/test) , the evaluation metric used was ROUGE and it generated a loss of nearly -3 and a RougeL Score of 0.2065, which could be improved by increasing the number of epochs to 5, it still generates some good one line summaries of news articles , even when news articles of different political bias is given as input, some amount of bias is removed in the final summary.


## Evaluation 
As a precursor to this project, I made a [News Bias Classifier](https://github.com/Wanderer-of-the-abyss/News-Bias-Discriminator) by fine-tuning pre-trained models like BERT, Roberta, DistillBERT, it generally has a good prediction rate, with an eval loss of 0.10 and accuracy of nearly 81% (further improvement can be dome using hyper-parameter tuining and testing with other models and techniques, as listed in [The Bipartisan Press](https://www.thebipartisanpress.com/politics/calculating-political-bias-and-fighting-partisanship-with-ai/)) . The classifier is used to check the text generated by the fine-tuned model for its political bias, which would futher help to improve the model.

## Other techniques to experiment with:

- incorporating adversarial training
- using reinforcement learning techniques like  RL-based sequence-to-sequence learning and actor - critic learning


