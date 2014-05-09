---
layout: post
title: "Customize your Octopress"
date: 2014-05-09 12:07:58 -0400
comments: true
categories: 
---
What's great about Octopress is that all the flexibility is right in your local files. It's only a matter of spending the time to customize it. 
<!--more-->

First customize the content:  
* Review and modify these [options](http://octopress.org/docs/blogging/)   
* Basic and simple [configurations](http://octopress.org/docs/configuring/)  
* Create a custom [CNAME](http://robdodson.me/blog/2012/04/30/custom-domain-with-octopress-and-github-pages/)  

Even though Octopress installs the default theme, it's easy to create your own changes or install 3rd party themes.      
* Here are the fields you can edit and customize the [theme](http://octopress.org/docs/theme/template/)  
* [Third Party Themes](https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes) you can install on your blog.   
* [Third Party Plugins](https://github.com/imathis/octopress/wiki/3rd-party-plugins)  
* [Coderwall: Make your own Theme](https://coderwall.com/p/g53gqq)  
* [Bill Patrianakos: Making of an Octopress Theme](http://billpatrianakos.me/blog/2012/10/31/the-making-of-an-octopress-theme/)
<br></br>
_______
###How to customize the current theme:
Octopress themes are based on [Jekyll](http://jekyllrb.com/) and [Shopify](http://www.shopify.com/) template language [Liquid](http://liquidmarkup.org/) (both written in Ruby). Learning some CSS and HTML will help you move forward. 

Themes are located in the `.themes/` folder and when you `rake install ["theme_name"]` it installs it to the folders:`sass` and `source`.
This essentially means you have 3 copies of an installed theme: 1. public repo 2. in `octopress` 3. in `.themes/`

Now we will walk through what files to customize: 

