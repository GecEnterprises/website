---
title: "My love and hate relationship with Go"
date: 2022-08-01T08:48:51+07:00
tags:
    - golang
    - language
    - programming
cover:
    image: /FastAndSimple.png
draft: true
---

> People already have mentioned about the points that I will bring up in this article, but I just wanted to try and explore my perspective and feelings (lol) towards this programming language as I'm writing this.

I first encountered the Go language back when I was contributing to the Google Code-In competition in 2019. During the time, I was only familiar with Node and a little bit of Java and C#. As time goes on, I use Go a lot at work but I also do use other languages as well during my freetime. 

> So what about now? You have used this language for one and a half years-ish?

That's true, but if I would point out where I am on my understanding for Go, it would be somewhere in the middle of the Slope of Enlightenment in the [Dunning-Kruger](https://en.wikipedia.org/wiki/Dunning%E2%80%93Kruger_effect) curve.

![The Dunning Kruger Curve](https://cdn.substack.com/image/fetch/w_1200,c_limit,f_jpg,q_auto:good,fl_progressive:steep/https://bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com/public/images/2cdd5572-88eb-46ed-8115-e7b20328eacb_1104x736.png)


But what do I mean by "understanding for Go" ? Go is a programming language, but a programming language is more than just syntaxes. A programming language can mean ecosystem, philosophy, performance, but most importantly: a tool.

If you ask me of my understanding for Go as a programming language in terms of syntax and ecosystem, it's probably in the middle of the Slope of Enlightenment, but if you ask me where my understanding of the philosophy of Go... I would struggle to answer. There are times where I really like Go for it's philosophy, and there are times where I simply don't understand it.


![Shinji Ikari's Pychographic Display](https://miro.medium.com/max/1270/0*Re9r7DpXJbN_RSXE.gif)

## Go understand the philosophy! Please!

> It's easy, the philosophy of Go is about **simplicity**

There are moments where I really love Go simply for it's simplicity (haha). However, as time goes on, while this "simplicity" mantra I found to be amazing in some aspects of the language, and some... not so great. You start building a software on something simple, but the more you iterate on it, the more complex it gets.

Many have pointed out that OOP language like [Java is way too verbose](https://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html) and I agree with it. OOP languages tends to hide the complexity, and that can give you a feeling of looking for a needle in a haystack.

So what does the approach that Go do? **Simplicity**.

But I keep thinking, is the simplicity that Go is aiming for is perfect? 

## The nitty-gritty

### Nullability

### Heavy reliance on Code Generation

### ... Generics?

### Struct tags

### Package Management

Go's approach of handling package management is by relying on the version control system (VCS) of that package.

### Error Handling

> TODO : Research Rust's Error Handling

## What do I think Go is perfect for



## So what are you really saying here?
I love Go. I hate Go. I love Go. I hate Go. I ... I'm not so sure. 

I am writing this article with the help of [hugo](https://github.com/gohugoio/hugo), a really awesome static site generator that allows you to convert Markdown files into HTMLs with theming support for the community. And this will be uploaded to my personal server running [caddy](https://github.com/caddyserver/caddy) a fast, multi-platform web server with automatic HTTPS.
