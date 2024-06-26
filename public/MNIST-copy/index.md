# MNIST Dataset


## MNIST Dataset
This project utilizes the [The Modified National Institute of Standards and Technology (MNIST) dataset](http://yann.lecun.com/exdb/mnist/) which comprises of 60 thousand training observations and 10 thousand test observations of handwritten digits.

## Image classification using neural networks with Python
Due to the complexity of imaging data, connectionist network models or neural networks have been gaining significant interest in recent years. Python machine learning packages ```sklearn``` and ```keras``` have been especially useful for specifying neural network architectures. This project aims to understand how connectionist models improve testing accuracy by varying the number of nodes in the hidden &#39;layer&#39; between one (actually not connectionist), two and 128 nodes. Expectedly, neural network models with 128 nodes in the hidden layer performed the best with 97% testing accuracy compared to 31%, 67% for the single node and double node models respectively. Understand the improvement in accuracy with these plots of the class distributions of the activation values in the hidden layer.

For a single node in the hidden layer (equivalent to logistic regression), we see some overlap:

![ClassDis1](/docs/singlenode.jpg)

Increasing the number of nodes in the hidden layer by one, we see better seperation between the classes:

![ClassDis2](/docs/twonodes.jpg)

See my [report](/docs/saraogee-research-report1.pdf) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; for further details. Also, see each experiment for each of the models ([single node](/docs/MSDS458_Assignment_01_exp1.html) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt;, [double node](/docs/MSDS458_Assignment_01_exp2.html) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt;, [many nodes](/docs/MSDS458_Assignment_01_exp3.html) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt;), as well as preprocessing inputs using [principal component analysis (PCA)](/docs/MSDS458_Assignment_01_exp4.html) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; or ranked inputs from a [random forest](/docs/MSDS458_Assignment_01_exp5.html) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; analysis.

## Image classification using random forests with Golang
This project creates a demo towards implementing a data engineering pipeline from image capture to recognition for an integrated application using purely Golang. For this demonstration, image classification is performed using Golang&#39;s [randomForest package](https://github.com/malaschitz/randomForest) employed on MNIST dataset using the [GoMNIST driver](https://github.com/kuroko1t/GoMNIST). Results are compared using an isolation forest ([go-iforest](https://github.com/e-XpertSolutions/go-iforest)) trained on all of the test observations.  For information about isolation forests, see an [earlier post](/PythonRGo) comparing Golang with Python/R under &#34;Identifying anomalies in MNIST&#34;. The best-performing model utilized 1000 trees and had **96% accuracy on the hold-out test dataset** with comparable accuracy for each digit. The average anomaly score was expectedly higher for the misclassified images. Misclassified images from the test set are printed using Go&#39;s [image package](https://pkg.go.dev/image).

To run locally, download or git clone this project:
```
git clone https://github.com/asaraog/msds431week10.git
cd msds431week10
./Week10
cd imagesout
ls
```
Images are printed in a new directory &#39;imagesout&#39; with the name coressponding to imageID, predicted digit, true digit and a boolean score for whether or not it is classified as anomalous. A csv file titled &#39;goScores.csv&#39; is also created with information for all of the images and an additional column for the anomaly score.

See my [Github repository](https://github.com/asaraog/msds431week10) for further details.

## References

Sambamoorthi, Nethra. &#34;Computer Vision,&#34;. MSDS 458: Artificial Intelligence and Deep Learning. Course at Northwestern University, Chicago, IL, October 9, 2022. https://github.com/aimlfacnwu/MSDS_458_Fall2022/tree/master/MSDS458_Assignment_01

Miller, Tom. &#34;Data Cleaning, Frames and Pipelines,&#34;. MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, June 19, 2023.

---

> Author:   
> URL: //localhost:1313/MNIST-copy/  

