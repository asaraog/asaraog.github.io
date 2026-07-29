---
title: Computer Vision in Python/Go
date: 2023-08-29T00:09:00-06:00
draft: false
projects: artificialintelligence
featuredImage: /images/vision.png

---
## Image classification using neural networks with Python
### MNIST dataset
This project utilizes the [The Modified National Institute of Standards and Technology (MNIST) dataset](http://yann.lecun.com/exdb/mnist/) which comprises of 60 thousand training observations and 10 thousand test observations of handwritten digits.

Due to the complexity of imaging data, connectionist network models or neural networks have been gaining significant interest in recent years. Python machine learning packages ```sklearn``` and ```keras``` have been especially useful for specifying neural network architectures. This project aims to understand how connectionist models improve testing accuracy by varying the number of nodes in the hidden 'layer' between one (actually not connectionist), two and 128 nodes. Expectedly, neural network models with 128 nodes in the hidden layer performed the best with 97% testing accuracy compared to 31%, 67% for the single node and double node models respectively. Understand the improvement in accuracy with these plots of the class distributions of the activation values in the hidden layer.

For a single node in the hidden layer (equivalent to logistic regression), we see some overlap:

<img src="/docs/singlenode.jpg" width="300" height="200">

Increasing the number of nodes in the hidden layer by one, we see better seperation between the classes:

<img src="/docs/twonodes.jpg" width="300" height="300">

See my [report](/docs/saraogee-research-report1.pdf) <i class="fa-solid fa-arrow-up-right-from-square"></i> for further details. Also, see each experiment for each of the models ([single node](/docs/MSDS458_Assignment_01_exp1.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>, [double node](/docs/MSDS458_Assignment_01_exp2.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>, [many nodes](/docs/MSDS458_Assignment_01_exp3.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>), as well as preprocessing inputs using [principal component analysis (PCA)](/docs/MSDS458_Assignment_01_exp4.html) <i class="fa-solid fa-arrow-up-right-from-square"></i> or ranked inputs from a [random forest](/docs/MSDS458_Assignment_01_exp5.html) <i class="fa-solid fa-arrow-up-right-from-square"></i> analysis.

### CIFAR-10 dataset
The growth of the mobile ecosystem has led to an unprecedented increase in the amount of digital imaging data. Alongside the considerable increase in computing power, deep learning neural networks are becoming an attractive option for computer vision applications in image classification. This study explores different network topologies and hyperparameters for traditional and convolutional neural networks using the [CIFAR-10 dataset (Canadian Institute of Advanced Research)](https://www.cs.toronto.edu/~kriz/cifar.html) of 60,000 images and 10 categories. The best performing model had a testing accuracy score of 78% and was with 3 hidden convolutional layers in a stacked topology with a fully connected layer and dropout regularization. Overall, convolutional neural network models performed better than traditional neural networks suggesting the suitability of convolution for computer vision applications. However, a key drawback is the high processing time in training models with convolutional layers.

See my [report](/docs/saraogee-research-report2-458.pdf) <i class="fa-solid fa-arrow-up-right-from-square"></i> for further details. Also, see the Jupyter notebooks for each experiment here:

|Experiment number	| Description|
| --- | ---|
|[1](/docs/exp1.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>|	2 layer deep neural network with 2000 neurons|
|[2](/docs/exp2.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>|	3 layer deep neural network with 2000 neurons|
|[3](/docs/exp3.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>|	2 layer deep convolutional neural network with 128, 256 neurons|
|[4](/docs/exp4.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>|	3 layer deep convolutional neural network with 128, 256, 512 neurons|
|[5](/docs/exp5.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>|	2 layer deep neural network with 2000 neurons and 0.3 dropout regularization|
|[6](/docs/exp6.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>|	3 layer deep neural network with 2000 neurons and 0.3 dropout regularization|
|[7](/docs/exp7.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>|	2 layer deep convolutional neural network with 128, 256 neurons and 0.3 dropout regularization|
|[8](/docs/exp8.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>|	3 layer deep convolutional neural network with 128, 256, 512 neurons and 0.3 dropout regularization|
|[9](/docs/exp9.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>| 2 layer deep convolutional neural network with 128, 256 neurons and 0.6 dropout regularization|
|[10](/docs/exp10.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>| 3 layer deep convolutional neural network with 128, 256, 512 neurons,  0.3 dropout regularization and a fully connected classification layer with 100 neurons|

#### Confusion matrix

The classification report and confusion matrix live inside each linked notebook. Pulling the best model's matrix ([experiment 10](/docs/exp10.html) <i class="fa-solid fa-arrow-up-right-from-square"></i>) out to where it can be read, with colour on **errors only** and a neutral diagonal.

<div class="cm-fig">
<img class="cm-light" src="/images/cifar_confusion_light.png" alt="CIFAR-10 confusion matrix for the best convolutional model, accuracy 78.27 percent over 10,000 test images. Largest confusions are dog predicted as cat (160), cat as dog (121), bird as deer (90), automobile as truck (82) and airplane as ship (78).">
<img class="cm-dark" src="/images/cifar_confusion_dark.png" alt="CIFAR-10 confusion matrix for the best convolutional model, accuracy 78.27 percent over 10,000 test images. Largest confusions are dog predicted as cat (160), cat as dog (121), bird as deer (90), automobile as truck (82) and airplane as ship (78).">
</div>

##### Precision and recall

| Class | Precision | Recall | F1 |
|---|---:|---:|---:|
| airplane | 0.821 | 0.771 | 0.795 |
| automobile | 0.954 | 0.859 | 0.904 |
| bird | 0.720 | 0.650 | 0.683 |
| cat | 0.599 | 0.636 | 0.617 |
| deer | 0.682 | 0.820 | 0.745 |
| dog | 0.742 | 0.680 | 0.709 |
| frog | 0.824 | 0.839 | 0.832 |
| horse | 0.871 | 0.765 | 0.815 |
| ship | 0.830 | 0.907 | 0.867 |
| truck | 0.827 | 0.900 | 0.862 |
| **Overall** | | | **78.27% accuracy** |

##### Top 5 errors

| Actual to predicted | Count |
|---|---:|
| dog to cat | 160 |
| cat to dog | 121 |
| bird to deer | 90 |
| automobile to truck | 82 |
| airplane to ship | 78 |


Nearly every large error is a within-superclass one. Cat and dog alone account for 281 errors between them, more than an eighth of all 2,173, and the rest pair vehicles with vehicles and animals with animals. Ship (0.907 recall) and automobile (0.859) are the easiest, cat (0.636) and bird (0.650) the hardest. The model has clearly learned the animal/vehicle split and is failing inside it.


## Image classification using random forests with Go
This project creates a demo towards implementing a data engineering pipeline from image capture to recognition for an integrated application using purely Go. For this demonstration, image classification is performed using Go's [randomForest package](https://github.com/malaschitz/randomForest) employed on [MNIST](http://yann.lecun.com/exdb/mnist/) dataset using the [GoMNIST driver](https://github.com/kuroko1t/GoMNIST). Results are compared using an **isolation forest** ([go-iforest](https://github.com/e-XpertSolutions/go-iforest)) trained on all of the test observations.  For information about isolation forests, see an [earlier post](/PythonRGo) comparing Go with Python/R under "Identifying anomalies in MNIST". The best-performing model utilized 1000 trees and had **96% accuracy on the hold-out test dataset** with comparable accuracy for each digit. The average anomaly score was expectedly higher for the misclassified images. Misclassified images from the test set are printed using Go's [image package](https://pkg.go.dev/image).

To run locally, download or git clone this project:
```
git clone https://github.com/asaraog/msds431week10.git
cd msds431week10
./Week10
cd imagesout
ls
```
Images are printed in a new directory 'imagesout' with the name coressponding to imageID, predicted digit, true digit and a boolean score for whether or not it is classified as anomalous. A csv file titled 'goScores.csv' is also created with information for all of the images and an additional column for the anomaly score.

See my [Github repository](https://github.com/asaraog/msds431week10) for further details.

### Confusion matrix

96% is one number covering ten quite different digits. This matrix comes from the model's own saved predictions in `goScores.csv`, with colour encoding **errors only** and a neutral diagonal so the error structure stays visible.

<style>
.cm-fig img.cm-dark { display: none; }
[data-theme="dark"] .cm-fig img.cm-light { display: none; }
[data-theme="dark"] .cm-fig img.cm-dark { display: block; }
.cm-fig img { max-width: 100%; height: auto; }
</style>
<div class="cm-fig">
<img class="cm-light" src="/images/mnist_confusion_light.png" alt="Confusion matrix for MNIST digit classification with a Go random forest. Accuracy 95.55 percent over 9,884 test images with 440 errors. Largest confusions are 4 predicted as 9 (28 times), 7 as 2 (27 times), and 5 as 3 (21 times).">
<img class="cm-dark" src="/images/mnist_confusion_dark.png" alt="Confusion matrix for MNIST digit classification with a Go random forest. Accuracy 95.55 percent over 9,884 test images with 440 errors. Largest confusions are 4 predicted as 9 (28 times), 7 as 2 (27 times), and 5 as 3 (21 times).">
</div>

#### Precision and recall

| Digit | Precision | Recall | F1 |
|---|---:|---:|---:|
| 0 | 0.953 | 0.990 | 0.971 |
| 1 | 0.987 | 0.988 | 0.987 |
| 2 | 0.948 | 0.946 | 0.947 |
| 3 | 0.946 | 0.949 | 0.948 |
| 4 | 0.964 | 0.952 | 0.958 |
| 5 | 0.955 | 0.938 | 0.946 |
| 6 | 0.960 | 0.971 | 0.966 |
| 7 | 0.964 | 0.940 | 0.952 |
| 8 | 0.945 | 0.939 | 0.942 |
| 9 | 0.930 | 0.939 | 0.934 |
| **Overall** | | | **95.55% accuracy** |

#### Top 5 errors

| Actual to predicted | Count | Why it is plausible |
|---|---:|---|
| 4 to 9 | 28 | a closed-top 4 is a 9 |
| 7 to 2 | 27 | a crossed or curved 7 mimics a 2 |
| 5 to 3 | 21 | an open-left 5 loses its stem |
| 8 to 9 | 18 | a faint lower loop |
| 7 to 9 | 15 | a shared descender stroke |


Digits 7 and 9 take 61 errors each and 8 takes 59 (recall 0.940, 0.939, 0.939), while 0 and 1 are essentially unconfusable. Every top confusion is a shape confusion a person would also make, so the forest fails on ambiguous glyphs rather than on a systematic fault.


## References

Sambamoorthi, Nethra. "Computer Vision Part 1". MSDS 458: Artificial Intelligence and Deep Learning. Course at Northwestern University, Chicago, IL, October 9, 2022. https://github.com/aimlfacnwu/MSDS_458_Fall2022/tree/master/MSDS458_Assignment_01

Sambamoorthi, Nethra. "Computer Vision Part 1". MSDS 458: Artificial Intelligence and Deep Learning. Course at Northwestern University, Chicago, IL, October 23, 2022. https://github.com/aimlfacnwu/MSDS_458_Fall2022/tree/master/MSDS458_Assignment_02

Miller, Tom. "Data Cleaning, Frames and Pipelines,". MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, June 19, 2023.