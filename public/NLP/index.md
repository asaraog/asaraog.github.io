# Natural Language Processing

# Deep Learning Classification Models with AG News
The growth of online news has led to a large volume of digital data. Natural language processing can help leverage this data for useful applications such as topic classification. Deep learning classification models are an attractive option to be used in these applications as the many layers in deep networks allow for hierarchal processing of the data (Glassner, 2021). The field of natural language processing has seen rapid growth since the advent of deep learning models with recurrent neural networks leading the charge (Ketkar &amp; Moolayil, 2021). 

A dataset from [AG News](http://groups.di.unipi.it/~gulli/AG_corpus_of_news_articles.html) of over 120,000 samples of news was classified according to topics - World, Sports, Business and Tech. Term frequency – inverse document frequency (TFIDF) is the classic method and is employed in this study for the vectorization of documents. [This study](https://github.com/aimlfacnwu/MSDS_458_Fall2022/blob/master/MSDS458_Assignment_03/MSDS458_Assignment_03_part02_SequenceModels_v6_20220906.ipynb) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; explores deep learning networks with a dataset of documents from AG News previously explored using convolutional neural networks by [others](https://github.com/Nyandwi/machine_learning_complete/blob/main/9_nlp_with_tensorflow/4_using_cnns_and_rnns_for_texts_classification.ipynb). The study compares various network architectures such as traditional neural networks and convolutional neural networks with varying network topologies and dropout percentage for regularization. Other research questions will include training time for the models. Transformer models, LSTM recurrent neural networks followed by convolutional neural networks have the lowest [error rate](https://paperswithcode.com/sota/text-classification-on-ag-news) on the AG News dataset. Initial studies with the AG News dataset employed convolutional neural networks and had about 90% testing accuracy. Newer LSTM based recurrent neural network models and transformer models had about 95% testing accuracy.  Indeed, recurrent neural networks, especially LSTM and bi-directional units, have become state-of-the-art in natural language processing applications (Ketkar &amp; Moolayil, 2021). 


## Medical Query Chatbot with DSM-5 data
**Abstract**

There is a growing shortage of manpower that can answer frequently asked questions in the medical field – both for patients and providers. Chatbots and automated assistants can leverage natural language processing techniques for useful interactions with humans and reduce the overall healthcare burden. A suitable corpus was derived from the Diagnostics and Statistical Manual of Mental Disorders, Fifth Edition (DSM-5) using the chapters related to anxiety disorders. Term frequency – inverse document frequency (TF-IDF) and a cosine similarity matrix is the classic method and is employed in this study for the vectorization of sentences and ranking of responses respectively. The logic and sensibility of responses were compared for five questions in each model. Various parameters were varied such as stop words for text preprocessing, differing corpus parameters as well as the inclusion of contextual sentences in the response. The best model utilized stop words preprocessing and the inclusion of an additional sentence for the user’s contextual understanding of the chatbot’s response. However, a key drawback is the requirement for using exact keywords in training chatbots with TF-IDF. Future studies would incorporate equivalent classes or embedding representations to gain deep semantic information.

See my [report](/docs/annotated-saraogee-453-researchreport4.pdf) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; and [presentation](/docs/annotated-453.pptx.pdf) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; for further details.

Also, see the Jupyter notebooks for each experiment here:

|Experiment number	| Description|
| --- | ---|
|[1](/docs/fexp1.html) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt;|	Stopword processing, single sentence output |
|[2](/docs/fexp2.html) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt;|	No stopword processing, signle sentence output|
|[3](/docs/fexp3.html) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt;|	Stopword processing, two sentence output |


## References
Dass, R. 2018. &#34;Create your chatbot using Python NLTK.&#34; Medium. https://medium.com/@ritidass29/create-your-chatbot-using-python-nltk-88809fa621d1

Glassner, Andrew. 2021. Deep Learning: A Visual Approach. No Starch Press. https://nostarch.com/deep-learning-visual-approach.

Ketkar, Nikhil, and Jojo Moolayil. 2021. “Recent Advances in Deep Learning.” In , 287–300. https://doi.org/10.1007/978-1-4842-5364-9_8.

Sambamoorthi, Nethra. &#34;Language Modeling with RNN&#34;. MSDS 458: Artificial Intelligence and Deep Learning. Course at Northwestern University, Chicago, IL, November 6, 2022. https://github.com/aimlfacnwu/MSDS_458_Fall2022/tree/master/MSDS458_Assignment_03

Srinivasan, Syamala. &#34;Creating Chatbot&#34;. MSDS 453: Natural Language Processing. Course at Northwestern University, Chicago, IL, December 4, 2022.

---

> Author:   
> URL: //localhost:1313/NLP/  

