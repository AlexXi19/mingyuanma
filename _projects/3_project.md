---
layout: page
title: Formalness
description:  Evaluate formal expression from 1000+ texts from Reddit using BERT-classifier and LogReg
img: assets/img/nlp/nlp.gif
importance: 2
category: work
---

### **Introduction**

The most exciting applications of NLP haven't been invented yet. While much of this course will give you exposure to the common methods in NLP, you will also carry out an annotation project where you will get exposure to the entire NLP design process for building a classifer for a brand new task. You will decide on a new NLP task — either document classification (one label per document) or sequence labeling (one label per contiguous span) — annotate data to support it (including creating annotation guidelines), measure your inter-annotator agreement rate, and build a classifier to predict those labels using the methods we discuss in class ([INFO 159, spring 2022](https://people.ischool.berkeley.edu/~dbamman/nlp22.html)). This is a group project, where I worked with my teammates, Yuanrui Zhu and Shuyao Zhou

In our AP project, the category we are annotating is a Reddit comment “casual”, “medium”, or “formal”. What we want to do is to subjectively map each comment to a numerical value 1~3, where 1 refers to "casual", 2 refers to "medium", and 3 refers to "formal."

The tentative guideline to give those scores (categories) is ceiling round up average score of three parts (subjective and may be more parts later), and each part would be rated 1~3. First, "Word" which based on the words they use (proportion of colloquial words, and the lexical level of the sentence); second, "structure" which based on the punctuations and the complexity of the sentence ("!" more likely to be casual and the more complex the sentence is the higher score it would get); third is the "character" of one sentence (eg. "I" would be personal which is less formal than "the author"). 

### **Annotation Guideline**

we have uploaded our final annotation guideline to [GitHub](https://github.com/Thunderbeee/NLP-attitude-score)

### **Data**

we get data from Reddit and clean @ [GitHub](https://github.com/Thunderbeee/NLP-attitude-score)

### **Modeling**

we use BERT-classifier and Logistic Regression (LogReg) in classification tasks

### **Analysis**

**Label Mistaken Identification** 

We plotted the confusion matrix comparing each class of actual and predicted test results, and accordingly calculated the Precision, Recall, and F-1 score for each of the four classes.


    ---
    For Class 0 (Casual), precision = 0.632, recall = 0.753, F1 = 0.687
    For Class 1 (Ordinary), precision = 0.379, recall = 0.2, F1 = 0.262
    For Class 2 (Formal), precision = 0.569, recall = 0.649, F1 = 0.607
    For Class 3 (Artistic), precision = recall = F1= 0
    ---

Analysis of statistics:

* For each class, its precision and recall are close. That is, for a class with high precision,
its recall is also high. So, clearly, there is a performance gap among the classes.
* The performance of Casual and Formal is much better than Ordinary, which follows the general case that the Ordinary class is a lot more difficult to classify than the other two classes. However, when putting a text to be in Class 1 (Ordinary), we may involve our personal judgment based on our unique educational and multilingual background. Hence, we're not classifying based on the same metrics as machines, and it's normal for
algorithms not to capture these factors and performing badly.
* The score of Casual is the highest among all the classes, which is largely due to the
apparent feature it demonstrates to readers (as we stated in the guideline).
* We observed that the logistic model tends to classify real Class 1 to Class 0/Class 2 since the precision for Class 1 is greater than its recall, which is the opposite case for Class 0 and Class 2. Given for the recall, real Y is in the denominator position, we can infer
Class 1 has nearly no apparent features that can be relied on.
* Because of the uneven nature of our dataset, precision and recall are all zero for Class 3,
which we will conduct further discussion in the following parts.

From the data set, we can clearly conclude that Class 1 (Ordinary) is often mistaken for Class 0 (Casual). Let's see why this would happen by looking at the example texts:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/nlp/pic2.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

There are fewer cases of the opposite, where the prediction is Class 1 when the actual category is Class 0:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/nlp/pic3.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Looking closely at the misclassification cases, we can tell that they're actually closer to Class 1 than we expected them to be. From the perspective of speakers, the person who says 'Next level reminds me of extreme movies’ and ‘Truelit and Truefilm are good though’ may very likely be in a casual state. We may have the wrong sense of those texts at the very beginning since we didn't quite get what the writer really wanted to express.

Beyond that, we would modify our guidelines boundary based on our observations. There're some sentences we would identify as "plain text", such as "I use a combination of Excel and Goodreads." We originally defined such “plain text” to be ordinary, but now we would choose to categorize them as Casual rather than Ordinary. We believe that besides "sentence structure", "sentence content" is another critical measurement of casualness. If the author explains a preference or a quick fact without any detailed discussion, this should be categorized as casualness of "sentence content", and thus it is casual overall.

One flaw of the training set and testing set is the imbalance of our data. Class 3 (Artistic) is rare, which puts some limitations on training, thus pushing the algorithm to ignore the underrepresented class entirely. Also, literary devices are very literal and are hard to learn from a small set of data. This explains why none of the three artistic labels in the test set are classified correctly. We should include more data in the training set to capture the internal patterns and rhetorical devices of the artistic paragraphs. Firstly, we get the percentage of each Class in the training set:

    ---
    Class 0 proportion (prior): 40.7%
    Class 1 proportion (prior): 26.83%
    Class 2 proportion (prior): 31.33%
    Class 3 proportion (prior): 1.17% 
    ---

At this point, one way to deal with this problem is randomly oversampling Class 3. We modified the classifier so it over-samples the underrepresented class and makes it approximately equal to the size of the most prevalent class. Now we reach the following accuracy:

    ---
    Class 0 proportion (posterior): 29.15%
    Class 1 proportion (posterior): 19.24%
    Class 2 proportion (posterior): 22.46%
    Class 3 proportion (posterior): 29.15%
    ---


**Features Learned to most define the Class (logistic regression)**

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/nlp/pic6.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

We will explain the strength of some features. For example, "!" / "?" are signs of strong sentiment, and "me" / "my" are signs of personal expression, which as we defined in the guideline: Are indicators of casualness. Furthermore, "as'' can be interpreted as "reasoning" and make sense to be a sign of Class 2. More "." in a document indicates that it is a longer text, which would be more likely to have detailed explanations and thus higher probability of formalness. Although Class 2 has the worst performance among all the classes, the defining features of Class 2 are still quite intuitive. "Dark", "world", and "love" are general intangible words that aren't usually used in formal expressions.

However, there are plenty of features that we wouldn't intuitively interpret as their strength. "Are" is a singular plural present tense of "be" which seems very prevalent in every kind of text in the real world, but here we only have it as a strong sign of formalness.

From the feature above, we also see something we didn’t carefully consider when selecting the data. We notice that for Class 1, "book", "literature", and "r/book" are among the top features of predictive power. This means there is a bias that the post we selected from the r/book thread is full of ordinary posts. Similarly, "r/truelit" and "r/askliterary studies' 'have a large proportion of formal posts, which makes them the defining feature of Class 2. This phenomenon is against our initial idea of only focusing on the text itself in order to grasp the feature of casualness-formalness. We believe changing the span of posts we analyze (also maybe removing any tags that exist in the post) can solve this issue to some extent.


##### We also tried to run data on BERT and made some observations:

*For keeping consistency with the BERT Jupyter Notebook, we will use Class 1 as Casual, Class 2 as Ordinary, Class 0 as Formal, and Class 3 as Artistic throughout this part. Note that this is different from our guidelines.*

Not satisfying with the result from logistic regression with self-defined feature above, we want to see if the deep learning model, BERT, considering the dependency of each words in one document and view the document as a whole, would perform better than the logistic regression which is feature-based using n-grams. Due to the GPU capacity issue of Google Colab, we changed the BERT model to "google/bert_uncased_L-2_H-128_A-2". After 25 Epoch, BERT achieved the test accuracy for best dev model: 0.610 with 95% Confidence Interval [0.542 0.678]. We can find that BERT performs better than the previous logistic regression. Although our self-defined features in the logistic regression model are the optimal ones after doing several trials, the BERT model can perform better than the logistic regression. This outstanding performance makes us understand the importance of viewing the document holistically when doing subjective judgment tasks. We should not emphasize certain words or certain pairs of words. Instead, as humans, we judge a sentence after reading it from start to the end. BoW or other n-grams cannot capture such nuance in sentences; otherwise, as what we mentioned above, it may overfit the data. So it is not surprising that BERT performs better: it works more similarly to how human perform classification tasks than n-grams. Although there is no feature in the deep learning model, BERT, we still want to delve into those misclassifications to see if we can observe any pattern.
We then generated a dictionary (key is the text, value is the (test_label, our_label) tuple pair) to compare the discrepancy between the test labels and our labels. Most of the differences are (1, 2) and (2, 0). We can know that Class 1 (Casual) is often mistaken for Class 2 (Ordinary). Also, Class 2 is often mistaken for Class 0 (Formal). This is expected because the boundaries between Class 2 and other classes were not strict. After examining the texts, we can tell that BERT has some biases. BERT would surprisingly classify some documents incorrectly.
12
For example, "Always happy to hear more people chime in! I know a big thing for all the contributors is knowing that people are actually reading and using posts/booklists/work. A little thank you goes a long way!Always happy to hear suggestions too. *Generally* we try to keep the bulk of recommendations from flaired members because it gives us a good idea of who's expertise is suggesting it. Not *super* sure what other avenues for volunteer work there is, other then as your using it let us know if you come across any problems. Broken links, typos, stuff like that.\n". BERT classifies it as Class 2 whereas we classified it as Class 1. It is surprising that BERT would misclassify this text. Obviously it would be Class 1 as there we can find informal words and exclamations which show the casual emotions. Such a basic classification task would be successfully done by a simple model, such as logistic regression whereas BERT may fail classifying it. Another phenomenon that BERT fails to consider is the group of internet slangs. This is also expected because internet slangs update very fast and hard to predict one from others. Also, BERT may not capture it correctly as a sign/feature of one class. However, we still believe that BERT would perform better if we have a more complex structure to capture those details and gain more useful information from documents.