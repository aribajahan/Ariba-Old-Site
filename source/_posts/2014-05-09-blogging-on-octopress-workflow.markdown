---
layout: post
title: "Blogging on Octopress Workflow"
date: 2014-05-09 03:39:29 -0400
comments: true
categories: 
---
Now that your blog is live, let's start creating content. 
<!--more-->

###Understanding Github <> Octopress
Octopress is a blogging platform created by [Brandon Mathis](http://brandonmathis.com/) which sits on top of Jekyll. Jekyll is a static site generator which uses the text files and converts them in to HTML. 

Octopress repositories have two branches: `source` and `master`. The `source` branch has the files needed to generate your blog while the `master` branch has the blog itself.

Right now, the source branch is where you cloned `Octopress` and it contains the `master` branch in the folder '_deploy'. So whenever you `git push origin source`,  the folders that begin with "_" are ignored. The `master` branch gets updated when you `rake deploy`. 

So your `master` branch on github.com is the '_deploy' folder. 

Going through some GIT tutorials can be helpful: [Git 101](http://jnakano.com/blog/uncategorized/github-101-an-intro-to-git/), [Git Workflow](https://www.atlassian.com/git/workflows#!workflow-forking), 

<br></br>
_______
###Customizing your Octopress:
+ Review and modify these [options](http://octopress.org/docs/blogging/) 
+ Basic and simple [configurations](http://octopress.org/docs/configuring/)
+ Here are the fields you can edit and customize the [theme](http://octopress.org/docs/theme/template/)
+ Create a custom [CNAME](http://robdodson.me/blog/2012/04/30/custom-domain-with-octopress-and-github-pages/)
+ [Third Party Themes](https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes) you can install on your blog. 
+ [Third Party Plugins](https://github.com/imathis/octopress/wiki/3rd-party-plugins)


<br></br>
_______
###Blogging Workflow
+ Keep a markdown cheatsheet open: [Cheatsheet1](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) or [Cheatsheet 2](https://github.com/NeQuissimus/MarkdownByExample/wiki/MarkdownSyntax) or [Code Nesting](http://meta.stackexchange.com/questions/3792/how-to-nest-code-within-a-list-using-markdown)
+ Keep your text editor, terminal, browser of choice on your dock. 
+ Open two tabs in terminal. One will be for previewing and the other for working. 
+ Bookmark these pages for further help: [Octopress](http://octopress.org/docs/) , [Custom Domain for Octopress](http://robdodson.me/blog/2012/04/30/custom-domain-with-octopress-and-github-pages/), [Octopress on Git](https://github.com/imathis/octopress), [Blogging Documentation](http://octopress.org/docs/blogging/)

<br></br>
_______
###Preview your Blog
+ In one terminal window. Keep this open: 
<pre><code>cd octopress
rake preview</code></pre>
+ Launch browser: localhost:4000. You can keep an eye on your edits by refreshing this.  

<br></br>
_______
###Create new post
+ In another terminal window, 
<pre><code>rake new_post["Title of your post"]</code></pre>
+ This will create the markdown file in the folder: octopress/source/_posts/
+ Now you can create your content here. 

<br></br>
_______
###Create new page
<pre><code>rake new_page[Title of your page]</code></pre>
+ This will create a folder with an index file. If you want this page to be on the navigation bar, you have to edit `/source/_includes/custom/navigation.html` file. 

<br></br>
_______
###Deploy
+ When you are satisfied, generate 
<pre><code>rake generate
rake deploy</code></pre>

+ If rake isn't working: 
<pre><code>build exec rake generate
build exec rake deploy</code></pre>

+ and Commit: 
<pre><code>git add .
git commit -am 'First commit'
git push origin source</code></pre>

<br></br>
_______
###Further Exploration: 
+ If you ever need to set up another computer to post to your existing blog, I'd follow [this](http://scottcheng.com/blog/2012/11/setting-up-existing-octopress-blog-on-a-new-computer/), [this](http://quibb.com/links/octopress-setting-up-a-blog-and-contributing-to-an-existing-one/view), [this](http://blog.zerosharp.com/clone-your-octopress-to-blog-from-two-places/) or [this](http://fernandomayer.github.io/blog/2013/03/02/configuring-octopress/)







