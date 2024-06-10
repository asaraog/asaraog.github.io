# MNIST Dataset


## MNIST Dataset
This project will utilize the The Modified National Institute of Standards and Technology (MNIST) dataset which comprises of 60 thousand training observations and 10 thousand test observations of handwritten digits.

## Image classification using neural networks with Python
See my [report](/docs/saraogee-research-report1.pdf) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; for further details.



## Image classification using random forests with Golang
See my [Github repository](https://github.com/asaraog/msds431week10) &lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; for further details.

This project aims to build an image processing demonstraion using Go looking to implement an OCR pipeline from image capture to recognition using classification. For this demonstration, classification is performed using random forests([randomForest](https://github.com/malaschitz/randomForest)) employed on MNIST dataset using the [GoMNIST driver](https://github.com/kuroko1t/GoMNIST). Results are compared using an isolation forest ([go-iforest](https://github.com/e-XpertSolutions/go-iforest)) trained on all of the test observations.  For information about isolation forests, see an [earlier post](/PythonRGo) comparing Golang with Python/R under &#34;Identifying anomalies in MNIST&#34;. The best-performing model utilized 1000 trees and had **96% accuracy on the hold-out test dataset** and comparable accuracy for each digit. The average anomaly score was expectedly higher for the misclassified images. Misclassified images from the test set are printed using Go&#39;s [image package](https://pkg.go.dev/image).

To run locally, download or git clone this project:
```
git clone https://github.com/asaraog/msds431week10.git
cd msds431week10
./Week10
cd imagesout
ls
```
Images are printed in a new directory &#39;imagesout&#39; with the name coressponding to imageID, predicted digit, true digit and a boolean score for whether or not it is classified as anomalous. A csv file titiled (&#39;goScores.csv&#39;)[./goScores.csv] is also created with information for all of the images and an additional column for the anomaly score.

## References

Sambamoorthi, Nethra. &#34;Computer Vision,&#34;. MSDS 458: Artificial Intelligence and Deep Learning. Course at Northwestern University, Chicago, IL, October 9, 2022. https://github.com/aimlfacnwu/MSDS_458_Fall2022/tree/master/MSDS458_Assignment_01

Miller, Tom. &#34;Image Processing,&#34;. MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, June 19, 2023.

---

> Author:   
> URL: //localhost:1313/Week7/  

