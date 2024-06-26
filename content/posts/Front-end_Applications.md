---
title: Front-end development in Go
date: 2023-08-22T00:09:00-06:00
draft: false
projects: dataengineering
featuredImage: /images/frontend.png

---

## What?

In the world of web and desktop applications, frameworks for different software languages such as [Rails](https://rubyonrails.org/) for Ruby and [Electron](https://www.electronjs.org/) for JavaScript are popular. Analogous to Rails, [Go](https://go.dev/) uses the [Wails](https://wails.io/) framework and offers the benefits of Go's reported processing speed. Wails also uses the native rendering engine unlike Electron which uses an embedded browser. Furthermore, Wails integrates user interface (UI) frameworks such as [React, Vue and Svelte](https://wails.io/docs/community/templates/).

To demo Go's frontend capabilities, two projects are implemented here using Wails and [Svelte](https://svelte.dev/repl/hello-world):
- Assisted Writing Application
- Chatbot

## Assisted Writing Application
This project produces a prototype for an assisted writing application based on [Vale](https://vale.sh/) (an exisiting command line interface written in Go).  It accepts plain text files (.txt or .md) as user input and a style preference as a text input. The output is displayed in the application with support for errors such as invalid user preference, invalid type of text file or insufficient length of text.The application prototype is succesful during development (wails dev) in linking Vale CLI output with user input and displaying errors. However, Wails is unable to integrate with command line applications during build (wails build) for this application. Future implemntations would explore other prose linters that do not require command line dependencies.

To run the prototype locally, first install Wails onto your machine and then download this project:
```
xcode-select --install
go install github.com/wailsapp/wails/v2/cmd/wails@latest
git clone https://github.com/asaraog/msds431week8.git
cd msds431week8
wails dev
```
To test for correct application behavior, input 1 or 2 to indicate a style preference and click 'Lint it' to upload 'test.txt'. Try entering 3 to generate the appropriate error message.

See my [Github repository](https://github.com/asaraog/msds431week8) for further details.

## Chatbot
This project produces a prototype for a desktop chatbot application. It accepts a single word query as a plain text input and output answers from a knowledge base([by others](https://github.com/ThomasWMiller/jump-start-sqlite/blob/main/QandA.csv)) represented with [Go's SQL](https://github.com/mattn/go-sqlite3) driver. The prototype is capable of integrating NLP concepts such as [term frequency-inverse document frequency (TF-IDF)](https://yi-wang-2005.medium.com/nlp-in-sql-word-vectors-82dffc908423). It also includes support for errors such as too many words, no input and no matches. The application prototype is succesful during development AND build in providing the correct answers to user input questions. Further development of the application would first continue in SQL by adding a TF-IDF representation to calculate similarity scores. We can then add 'fuzzy matching' and tokenization/lemmatization of the corpus and query. This will have the simplest development process with no dependency required. The single word query is highly amenable to using word2vec.

To run the application locally, download or git clone this project:
```
git clone https://github.com/asaraog/msds431week9.git
cd msds431week9/build/bin
open Week9.app
```
To test for correct chatbot application behavior first type nothing into the text box and then 'break', 'test' and 'break test' before clicking 'Query'

See my [Github repository](https://github.com/asaraog/msds431week9) for further details.

## References

Miller, Tom. "Desktop Applications,". MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, June 19, 2023.

Miller, Tom. "Natural Language Processing,". MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, June 19, 2023.
https://github.com/ThomasWMiller/jump-start-sqlite