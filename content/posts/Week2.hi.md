---
weight: 1
title: Comparing Golang with Python/R
date: 2024-05-08T00:09:00-06:00
draft: false
datascience: गोलांग
featuredImage: /images/comparing.png

---
<font size="1"> Image credit: [R logo](https://www.r-project.org/logo/), [Gopher](https://go.dev/doc/gopher/README) </font>

## Evaluating Go

[Golang](https://go.dev/) is a compiled language that is more verbose but is said to run faster compared to R/Python. Here, Golang's performance and runtime is benchmarked against Python and/or R with various cases:

1. Performing least squares regression of the [Anscombe Quartet (1973)](https://www.sjsu.edu/faculty/gerstman/StatPrimer/anscombe1973.pdf)
2. Computing summary statistics of the [California Housing Prices (Miller 2015)](https://github.com/mtpa/mtpa/tree/master/MTPA_Chapter_10)
3. Web crawling and scraping of [Wikipedia](https://en.wikipedia.org/)
4. Identify anomalies in the [MNIST dataset](http://yann.lecun.com/exdb/mnist/)

### Least squares regression with Python and R
See [Github repository](https://github.com/asaraog/msds431week2) for further details.

The Golang implementation is benchmarked for runtime with a [previous implementation by Miller (2015)](https://github.com/mtpa/mtpa/tree/master/MTPA_Chapter_1) in Python/R as a reference. Least squares regression is implemented in Golang using the [stats package](https://github.com/montanaflynn/stats). Python was significantly slower compared to R and Go implementations with runtimes of 1.36s, 0.04s, 0.173s for Python, R and Go. While R was less verbose and a bit faster than Go, Go's testing package ensured identitcal least squares coefficients of 0.5 and 3 for each Anscombe dataset during development.

### Summary statistics with Python and R
See [Github repository](https://github.com/asaraog/msds431week4) for further details.

The Golang implementation is done using the [stats package](https://github.com/montanaflynn/stats). Runtimes are compared using 'time' before commands in the command line to compare with Python's pandas.describe() and R's summary functions. The operations are run 100 times for each implementation. Python was significantly faster compared to R and Go implementations with 'real' runtimes of 2.27s, 4.10s, 5.02s for Python, R and Go respectively. While Python and R were less verbose and a bit faster than Go, Go's testing package ensured similar summary statistics as Python for each of the seven variables (value, income, age, rooms, bedrooms, pop, hh) during development. 

### Web crawling and scraping with Python
See [Github repository](https://github.com/asaraog/msds431week5) for further details.

This project implemented web crawling and scraping of Wikipedia [(described by Chanda 2021)](https://www.scrapingbee.com/blog/web-scraping-go/#building-a-basic-scraper) webpages in Golang using [Colly](https://go-colly.org/). The Go implementation is benchmarked for runtime using 'time' before commands in the command line to compare with Python's implementation for the same 10 webpages using [scrapy](https://github.com/scrapy/scrapy). Python was significantly slower compared Go implementations with 'real' runtimes of 15.9s and 0.6s for Python and Go respectively. While Python was less verbose than Go, Go is more scalable and has concurrency support to allow for even faster processing using [Colly](https://go-colly.org/docs/examples/parallel/).

### Identifying anomalies using isolation forests with Python and R
See [Github repository](https://github.com/asaraog/msds431week7) for further details.

Isolation forests are used as an unsupervised learning method to identify anomalies or outliers. It was introduced by [Liu 2008](https://cs.nju.edu.cn/zhouzh/zhouzh.files/publication/icdm08b.pdf) by observing that path lengths for anomalies were significantly SHORTER by averaging over many trees. He introduces an anomaly score to normalize comparisons with HIGHER scores indicating more abnormality. Hyperparameters were kept the same across languages with 1000 trees and 256 samples. The [go-iforest](https://github.com/e-XpertSolutions/go-iforest) package was used for the analysis in Go. Comparison code for R and Python was adapted from [Miller 2023](https://github.com/ThomasWMiller/jump-start-mnist-iforest).
Runtimes were significantly lower in Golang with runtimes of 5.66s, 19.02s, and 1m 42.87s for Golang, R and Python respectively. This is likely due to the goroutines utilized in the go-iforest package.

## Overview

Programs written using Golang had similar performances to Python/R in basic statistical learning applications such as least squares regression and summary statistics. Efficient results were obtained utilizing test-driven development. In applications with more scalability, Golang performed very well. For both web scraping/crawling and identifying anomalies, Golang performs more than 10 times faster than Python. This could be attributed to Golang's concurrency support with goroutines.

## References

Anscombe, F. J. 1973. “Graphs in Statistical Analysis.” The American Statistician 27 (1): 17–21. https://doi.org/10.2307/2682899.

Chanda, Subha. 2021. “Web Scraping with Go.” ScrapingBee. 2021. https://www.scrapingbee.com/blog/web-scraping-go/. 

Liu, Fei Tony, Kai Ming Ting, and Zhi-Hua Zhou. 2008. [“Isolation Forest.”](https://cs.nju.edu.cn/zhouzh/zhouzh.files/publication/icdm08b.pdf). In ICDM '08: Proceedings of the 2008 Eighth IEEE International Conference on Data Mining, December 2008, 413–422.

Miller, Tom. "Testing Go for Statistics,". MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, June 19, 2023.

Miller, Tom. "Working with Data Frames,". MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, June 19, 2023.

Miller, Tom. "Command-Line Applications,". MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, July 1, 2023.

Miller, Tom. "Crawling and Scraping the Web,". MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, July 2, 2023.


