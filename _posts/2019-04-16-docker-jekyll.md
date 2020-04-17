---
layout: post
title: Install Jekyll + Docker to run Github Pages locally
---

![Docker Jekyll Cover](/images/jekyll-docker.png)

Already built Jekyll person website!!! Want to test this on local machine?? Then this article is right for you.

## Introduction

After a long time spent on busy university life and other projects, I have decided to get back to writing blogs. In order to publish blogs effectively, I need to run the my personal <b>Jekyll</b> website locally. Initially, I followed **[these steps](https://jekyllrb.com/docs/installation/macos/)** to install Jekyll with <b>gem</b> commands on my Macbook Pro 2016 (Catalina OS). However, I have not been successful at all after many failed attempts (<b>see my terminal output below</b>). Therefore, I will come with my next approach of using Docker to run Jekyll website locally.

![Install Jekyll Terminal](/images/install-jekyll-mac.png)

## Running Jekyll With Docker

<b>Docker</b> is a helpful tool for packing, shipping and running applications within "<b>containers</b>". In this context, I will use <b>Docker Compose</b> to run my wesite container in local environment. See the config in my <b>docker-compose.yml</b> file.

<script src="https://gist.github.com/tranquanghuy0801/0487d4a7cb82524abb68802b14294db6.js"></script>

As can be seen from the config file, I utilized the <b>Docker</b> image from this **[link](https://github.com/Starefossen/docker-github-pages)** for the <b>Jekyll</b> service. Customize your container name and add the Github Token from following **[these steps](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line)**. Finally, running the command "<b>docker-compose up</b>" on Terminal and then your container is deployed successfully. Additionally, it also can update the latest changes in your project folder (how <b>amazing</b> this is!!!) 

View your website at <http://127.0.0.1:4000/>.

## Conclusion

If you have read until this line, I am appreciated your support for my blog. Stay tuned and looking forward to my next article!!!
