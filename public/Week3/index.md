# Using Golang to Build a Website

## Why?

[Golang](https://go.dev/) is a compiled language designed for today&#39;s multi-processor, scalable, high-performance systems. Known for efficient real-time data processing, [Uber](https://github.com/uber-go/guide) uses Golang on the backend. Static site generators such as [Hugo](https://gohugo.io) were developed recently using Golang. Other platforms have inherited dependency chains that can lead to infeasible build times. For example, [Cloudfare](https://blog.cloudflare.com/new-dev-docs) recently migrated from Gatsby.

### Demo

I created a [demo website](autonotes.netlify.app) using the [Hugo Winston theme](https://themes.gohugo.io/themes/hugo-winston-theme/). This theme does have a [Live Demo](https://hugo-winston.netlify.app/) which made it simple to deploy from [Github](https://github.com/asaraog/msds431week3) onto [Netlify](https://www.netlify.com/). All descriptions are fictional and generated using [ChatGPT](https://chat.openai.com/).

### Saraogee.com

I had several requirements in mind for my website:
- Public Comments such as [Valine](https://valine.js.org/en/)
- Site Analytics such as [Google Analytics](https://developers.google.com/analytics/)
- Search such as [Fuse.js](https://www.fusejs.io/)

The [FixIt](https://themes.gohugo.io/themes/fixit/) theme was a great starting point for my website. After some changes to the layout categories and adding support for [Hindi](https://github.com/hugo-fixit/FixIt/commit/dfeaf0e9a7c2a34e32b259e41dd4d48dfdb61ae7), I deployed the website using [Github Pages](https://github.com/asaraog/asaraog.github.io/deployments) to my custom domain saraogee.com.

## Try it yourself

**1. Install Hugo**

Please follow the official [installation guide](https://gohugo.io/getting-started/installing/).

**2. Import Hugo site locally**

Download or git clone this project onto local machine into folder on local machine.

```
git clone https://github.com/asaraog/msds431week3.git
cd msds431week3
cd exampleSite
hugo server
```
or

```
git clone https://github.com/asaraog/asaraog.github.io.git
cd asaraog.github.io
hugo server
```

**3. Deploy it**

Now enter [`localhost:1313`](http://localhost:1313) in the address bar of your browser. Files can then be changed and then committed/pushed when complete to git. Once pushed to git, the website can be deployed.

## References
Jain, Atishay. 2022. Hugo in Action: Static Sites and Dynamic Jamstack Apps. https://learning.oreilly.com/library/view/hugo-in-action/9781617297007/.

Miller, Tom. &#34;Setting Up a Website,&#34;. MSDS 431: Data Engineering with Go. Course at Northwestern University, Chicago, IL, June 9, 2023.


---

> Author:   
> URL: //localhost:1313/Week3/  

