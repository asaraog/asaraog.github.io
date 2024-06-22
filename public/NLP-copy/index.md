# Natural Language Processing

## Deep Learning Classification Models with AG News
The volume of digital data such as online news has been growing at an unprecedented pace. Natural language processing can help leverage this data for useful applications such as topic classification. A dataset from AG News of over 120,000 samples of news was classified according to topics - World, Sports, Business and Tech. Term frequency – inverse document frequency (TFIDF) is the classic method and is employed in this study for the vectorization of documents. Various deep learning models were utilized including traditional neural networks, and convolutional neural networks (CNN). Network architecture including number of neurons and other hyperparameters including regularization were varied. This highest accuracy model (78%) was with a 3 layer deep convolutional neural network with 128, 256, 512 neurons and 0.6 dropout regularization. However, a key drawback is the high processing time in training models with TFIDF. Future studies would focus on word embeddings.

See my [report](/docs/saraogee-research-report5.pdf) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; and [Jupyter notebook](/docs/Assignment5.html) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; for further details. 

## Medical Query Chatbot with DSM-5 data
There is a growing shortage of manpower that can answer frequently asked questions in the medical field – both for patients and providers. Chatbots and automated assistants can leverage natural language processing techniques for useful interactions with humans and reduce the overall healthcare burden. A suitable corpus was derived from the Diagnostics and Statistical Manual of Mental Disorders, Fifth Edition (DSM-5) using the chapters related to anxiety disorders. Term frequency – inverse document frequency (TF-IDF) and a cosine similarity matrix is the classic method and is employed in this study for the vectorization of sentences and ranking of responses respectively. The logic and sensibility of responses were compared for five questions in each model. Various parameters were varied such as stop words for text preprocessing, differing corpus parameters as well as the inclusion of contextual sentences in the response. The best model utilized stop words preprocessing and the inclusion of an additional sentence for the user’s contextual understanding of the chatbot’s response. However, a key drawback is the requirement for using exact keywords in training chatbots with TF-IDF. Future studies would incorporate equivalent classes or embedding representations to gain deep semantic information.

See my [report](/docs/saraogee-research-report5.pdf) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; and [Jupyter notebook](/docs/Assignment5.html) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; for further details. 

## References

Sambamoorthi, Nethra. &#34;Language Modeling with RNN&#34;. MSDS 458: Artificial Intelligence and Deep Learning. Course at Northwestern University, Chicago, IL, November 6, 2022. https://github.com/aimlfacnwu/MSDS_458_Fall2022/tree/master/MSDS458_Assignment_03

Srinivasan, Syamala. &#34;Creating Chatbot&#34;. MSDS 453: Natural Language Processing. Course at Northwestern University, Chicago, IL, December 4, 2022.

---

> Author:   
> URL: //localhost:1313/NLP-copy/  

