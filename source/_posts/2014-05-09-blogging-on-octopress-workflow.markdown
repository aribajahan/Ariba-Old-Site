---
layout: post
title: "Blogging on Octopress Workflow"
date: 2014-05-09 03:39:29 -0400
comments: true
categories: 
---
Now that your blog is live, let's understand how Octopress works and start creating content. 
<!--more-->
###Quick Summary of how to generate-deploy-commit
<pre><code>
	cd octopress
	rake new_post["Title of post"]
	rake generate 
	rake deploy

	git add .
	git commit -am 'Message to commit'
	git push origin source
</code></pre>

###Understanding Github <> Octopress
Octopress is a blogging platform created by [Brandon Mathis](http://brandonmathis.com/) which sits on top of Jekyll. Jekyll is a static site generator which uses the text files and converts them in to HTML.   

Octopress repositories have two branches: `source` and `master`. The `source` branch has the files needed to generate your blog while the `master` branch has the blog itself.  

Right now, the source branch is where you cloned `Octopress` and it contains the `master` branch in the folder '_deploy'. So whenever you `git push origin source`,  the folders that begin with "_" are ignored. The `master` branch gets updated when you `rake deploy`.   

So your `master` branch on github.com is the '_deploy' folder.   

Going through some GIT tutorials can be helpful: [Git 101](http://jnakano.com/blog/uncategorized/github-101-an-intro-to-git/) and [Git Workflow](https://www.atlassian.com/git/workflows#!workflow-forking)  

_______
###Understand your Repo:
If you spend some time to understand this now, it'll help you troubleshoot and better understand exactly what happens. 
<pre><code>
	cd octopress #the repo where you cloned octopress
	git remote show origin

	* remote origin
	Fetch URL: https://github.com/aribajahan/aribajahan.github.io.git
  	Push  URL: https://github.com/aribajahan/aribajahan.github.io.git
  	HEAD branch: master
  	Remote branches:
    master new (next fetch will store in remotes/origin)
    source tracked
  	Local branch configured for 'git pull':
    source merges with remote master
  	Local ref configured for 'git push':
    source pushes to source (up to date)
</code></pre>

<pre><code>
	cd octopress/_deploy/ #the repo within your source folder
	git remote show origin

	* remote origin
  	Fetch URL: https://github.com/aribajahan/aribajahan.github.io.git
  	Push  URL: https://github.com/aribajahan/aribajahan.github.io.git
  	HEAD branch: master
  	Remote branches:
    master tracked
    source tracked
  	Local ref configured for 'git push':
    master pushes to master (up to date)
</code></pre>

So now you can see exactly what repo is the `source` and `master` and where they push. They are the 2 separate branches of your github page main repo.


_______
###Blogging Workflow
+ Keep a markdown cheatsheet open: [Cheatsheet1](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) or [Cheatsheet 2](https://github.com/NeQuissimus/MarkdownByExample/wiki/MarkdownSyntax) or [Code Nesting](http://meta.stackexchange.com/questions/3792/how-to-nest-code-within-a-list-using-markdown)
+ Keep your text editor, terminal, browser of choice on your dock. 
+ Open two tabs in terminal. One will be for previewing and the other for working. 
+ Bookmark these pages for further help: [Octopress](http://octopress.org/docs/) , [Custom Domain for Octopress](http://robdodson.me/blog/2012/04/30/custom-domain-with-octopress-and-github-pages/), [Octopress on Git](https://github.com/imathis/octopress), [Blogging Documentation](http://octopress.org/docs/blogging/)

_______
###Preview your Blog
In one terminal window. Keep this open:   
<pre><code>cd octopress
rake preview</code></pre>
Launch internet browser: Type `localhost:4000` in the address. You can keep an eye on your edits by refreshing this as you test out your markdown skills.  

_______
###Create new post
In another terminal window, 
<pre><code>rake new_post["Title of your post"]</code></pre>  
This will create the markdown file in the folder: `octopress/source/_posts/`  
Now you can write your post in that markdown file. 

_______
###Create new page
<pre><code>rake new_page[Title of your page]</code></pre>  
This will create a folder with an index file. If you want this page to be on the navigation bar, you have to edit `/source/_includes/custom/navigation.html` file. 

_______
###Deploy
When you are satisfied, generate   
<pre><code>rake generate
rake deploy</code></pre>  

If rake isn't working:   
<pre><code>build exec rake generate
build exec rake deploy</code></pre>  

Commit:   
<pre><code>git add .
git commit -am 'First commit'
git push origin source</code></pre>


_______
###Further Troubleshooting: 
- If you ever need to set up another computer to post to your existing blog, I'd follow [this](http://scottcheng.com/blog/2012/11/setting-up-existing-octopress-blog-on-a-new-computer/), [this](http://quibb.com/links/octopress-setting-up-a-blog-and-contributing-to-an-existing-one/view), [this](http://blog.zerosharp.com/clone-your-octopress-to-blog-from-two-places/) or [this](http://fernandomayer.github.io/blog/2013/03/02/configuring-octopress/)  
- If you ever lose the source to your blog, check out [his solution](http://blog.pezholio.co.uk/2013/04/lost-the-source-to-my-octopress-blog-ooops/).  
- If you are interested in hosting your site on [Amazon 3](http://www.julianbonilla.com/blog/2012/11/05/octopress-on-amazon-s3/).   

###If you are looking for more resources, Check out:  
[AlBlue's Advatanges of Octopress](http://alblue.bandlem.com/2012/02/advantages-of-octopress.html)  
[Why Octopressby Paul Rayner](http://thepaulrayner.com/blog/2013/02/04/blogging-with-octopress-and-github-pages/)  
[Matt Gemmell's Blogging with Octopress](http://mattgemmell.com/blogging-with-octopress/)  
[Terry's Octopress Wiki](http://terry.im/wiki/terry/Octopress.html)  
[Hiltmon's 18 months of Octopress](http://hiltmon.com/blog/2013/04/17/18-months-of-octopress/)  
[Hiltmon's script on isolating post for preview](http://hiltmon.com/blog/2012/07/18/octopress-post-and-publish/)  
[Octopress Themes FAQ](http://octopressthemes.com/faq/)  
[Ryan Deussing's Tutorials](http://ryandeussing.com/)
[Octopus: A Jekyll+ Octopress Command line help](http://chrissimpkins.github.io/octopus/)  
[Octopress with Django](http://www.viggiosoft.com/blog/blog/2011/09/28/setting-up-a-blog-with-octopress/)
[Migrate Wordpress to Octopress](http://www.dinduks.com/yet-another-blog-that-migrates-to-octopress/)  







