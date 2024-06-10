---
weight: 3
title: Concurrency with Golang
date: 2024-05-15T00:09:00-06:00
draft: false
datascience: गोलांग
featuredImage: /images/concurrent.png

---
<font size="1"> Image credit: [R logo](https://www.r-project.org/logo/), [Gopher](https://go.dev/doc/gopher/README) </font>

## What?

Concurrency is breaking up a single process into independent components and then making a plan on how they will compute. It is based on the idea of CSP or Communicating Sequential Processes (Brookes, Hoare, and Roscoe 1984). The paradigm here is shifted towards communication and splitting of independent processes instead of sharing memory in parallel processing. To communicate between different processes, Golang utilizes goroutines, which are similar to channels as described in CSP. These are different from threads and more lightweight.

## Linear Regression
See [Github repository](https://github.com/asaraog/msds431week6) for further details.

This project evaluated Go's concurrent programming framework for training and testing linear regression models. Machine learning models will utilize the [gonum library](https://pkg.go.dev/gonum.org/v1/gonum). The Go implementation tested linear regression models with varying regulization and/or concurrency using the [Boston Housing Study (1970)](http://lib.stat.cmu.edu/datasets/boston), commonly used by statisticians to predict housing prices by others (Brownlee 2020). This dataset was modified by others (Miller 1999) to remove the feature 'B' encoding racial segregation. All models were run 100 times and benchmarked for runtime using 'time' before commands in the command line and the concurrency flag 0 or 1. Concurrency significantly increased speed with a runtime of 0.009s compared to 0.279s without concurrency.

### Running the demo locally

Download or git clone this project onto local machine into folder on local machine.
```
git clone https://github.com/asaraog/msds431week6.git
cd msds431week6
time ./Week6 -concurrency 0
time ./Week6 -concurrency 1

```

## References

Brookes, S. D., C. A. R. Hoare, and A. W. Roscoe. 1984. “A Theory of Communicating Sequential Processes.” Journal of the ACM 31 (3): 560–99. https://doi.org/10.1145/828.833.

Brownlee, Jason. 2020. “How to Develop Ridge Regression Models in Python.” MachineLearningMastery.Com (blog). October 8, 2020. https://machinelearningmastery.com/ridge-regression-with-python/.

Miller, Thomas W. 1999. "The Boston splits: Sample size requirements for modern regression." 1999 Proceedings of the Statistical Computing Section of the American Statistical Association, 210–215.

