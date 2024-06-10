# Front-End Development With Golang


## What?

Analogous to [Rails](https://rubyonrails.org/) for Ruby, Golang has [Wails](https://wails.io/) for front-end application development. Popular front-end frameworks for JavaScript such as [React, Angular and Vue](https://wails.io/docs/community/templates/) can be used with Wails. Built on Golang, Wails uses the native rendering engine rather than an embedded browser (https://www.electronjs.org/)

[Svelte](https://svelte.dev/repl/hello-world) is a lighter and beginner-friendly front-end framework. Wails and Svelte are used for two projects:
- Assisted Writing Application
- Chatbot 

To install Wails onto your machine:
```
xcode-select --install
go install github.com/wailsapp/wails/v2/cmd/wails@latest
```

## Assisted Writing Application
See my [Github repository](https://github.com/asaraog/msds431week8)&lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; for further details.

This project produces a prototype for an assisted writing application based on [Vale](https://vale.sh/) (an exisiting command line interface written in Golang).  It accepts plain text files (.txt or .md) as user input and a style preference as a text input. The output is displayed in the application with support for errors such as invalid user preference, invalid type of text file or insufficient length of text.The application prototype is succesful during development (wails dev) in linking Vale CLI output with user input and displaying errors. However, Wails is unable to integrate with command line applications during build (wails build) for this application. Future implemntations would explore other prose linters that do not require command line dependencies.

To run locally, download or git clone this project:
```
git clone https://github.com/asaraog/msds431week8.git
cd msds431week8
wails dev
```

## Chatbot
See my [Github repository](https://github.com/asaraog/msds431week9)&lt;i class=&#34;fa-solid fa-arrow-up-right-from-square&#34;&gt;&lt;/i&gt; for further details.

This project produces a prototype for a desktop chatbot application. It accepts a single word query as a plain text input and output answers from a knowledge base([by others](https://github.com/ThomasWMiller/jump-start-sqlite/blob/main/QandA.csv)) represented with [Go&#39;s SQL](https://github.com/mattn/go-sqlite3) driver. The prototype is capable of integrating NLP concepts such as [term frequency-inverse document frequency (TF-IDF)](https://yi-wang-2005.medium.com/nlp-in-sql-word-vectors-82dffc908423). It also includes support for errors such as too many words, no input and no matches. The application prototype is succesful during development AND build in providing the correct answers to user input questions. Further development of the application would first continue in SQL by adding a TF-IDF representation to calculate similarity scores. We can then add &#39;fuzzy matching&#39; and tokenization/lemmatization of the corpus and query. This will have the simplest development process with no dependency required. The single word query is highly amenable to using word2vec.

To run locally, download or git clone this project:
```
git clone https://github.com/asaraog/msds431week9.git
cd msds431week9/build/bin
open Week9.app
```
Before clicking &#39;Query&#39;, input nothing, &#39;break&#39;, &#39;test&#39; and &#39;break test&#39; in the text box to check for correct application behavior.

## References

Miller, Tom. &#34;Desktop Applications,&#34;. MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, June 19, 2023.

Miller, Tom. &#34;Natural Language Processing,&#34;. MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, June 19, 2023.
https://github.com/ThomasWMiller/jump-start-sqlite

---

> Author:   
> URL: //localhost:1313/Week8/  

