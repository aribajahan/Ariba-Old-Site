---
layout: post
title: "Create your own Octopress blog"
date: 2014-05-09 00:57:04 -0400
comments: true
categories: octopress, github, blogging
---

Here is the thing, I never even knew what github was. To get over that, I decided I would learn not only learn github but launch an octopress blog. So here is how you can make yours. 

Disclaimer: I had to rebuild this THREE times. So, definitely do not get discouraged (especially if you are a newbie, like me). 

<!--more-->

###Workflow on Mac
1. Open Terminal *(I suggest you place a shortcut to Terminal on your dock)*
2. Download a text editor. I use [Sublime Text](http://www.sublimetext.com/)
3. Install [Git](http://git-scm.com/downloads) *Assuming you already have a [github](github.com) account*

###Before you get started
1. Check Ruby version, on command line: `Ruby -v`
2. Check git version, on command line: `Git -v`
   The latest Ruby version is 2.1.1. If you have this or 1.9.3, you are set. If not, you have to install Ruby. 
   This should tell you if you installed Git correctly. 
___
###Install RVM and Ruby
* RVM is designed to help you manage the different Ruby versions and gems. 
* It's pretty neat how many of these installations have been scripted which makes it easier for us to install it all.
<pre><code>curl -L get.rvm.io | bash -s stable</code></pre> 

* Then, we need to make sure that RVM gets loaded in all of our shells (terminal windows). 
* Type `nano .bash_profile`
* The file will load up right in terminal. Scroll to the bottom and add the following text: 
<pre><code>[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" </code></pre> 
* Save this by pressing `ctrl+o` ,then `return`
* Exit nano by pressing `ctrl+x`

* Now, quit terminal and restart. To check if this worked `rvm -v`
* This should show you the running version of RVM. 

* Install Ruby `rvm install 2.1.1`
* `rvm use 2.1.1`
* Should say >> Using /Users/aribajahan/.rvm/gems/ruby-2.1.1

* Check ruby version: `ruby -v`
* Let's tell rvm to set this ruby as default: `rvm use 2.1.1 --default`

###Now let's setup all of our gemsets
* `rvm gemset create my-new-gemset`
* Let's go to that gemset location: 
<pre><code>cd /Users/aribajahan/.rvm/gems/ruby-2.1.1@my-new-gemset
	ls</code></pre>
* Let's default the ruby version: `rvm 2.1.1@my-new-gemset --default`
* You should be in the gem directory. Now, `gem install nokogiri`
* Let the gemset install. 

* Now `cd gems`
* Let's see how many gems got installed: `ls`

* Now, let's install Rails. 
<pre><code>rvm gemset create my-new-rails-setup</code></pre>
Should show: `ruby-2.1.1 - #gemset created /Users/aribajahan/.rvm/gems/ruby-2.1.1@my-new-rails-setup`
`ruby-2.1.1 - #generating my-new-rails-setup wrappers.........`

* This assigns this Ruby version to the gemset: `rvm 2.1.1@my-new-rails-setup`
* Now, let's install Rails: `gem install rails`
_This will take some time_

* Let's see if it all installed: `cd gems`
* Reveal the list of gems: `ls`
* You should see far more gems now. 

###Ok, now we are ready to install Octopress
* Create Octopress gem
* `rvm gemset create octopress`
* `rvm 2.1.1@octopress`

####Clone and Install
<pre><code>git clone git://github.com/imathis/octopress.git octopress
cd octopress </code></pre> 
_Note: you can name the folder anything instead of 'octopress'._

* Now let's use rvmrc to assign Ruby to this folder. 
`>.rvmrc
echo "rvm use 2.1.1@octopress"> .rvmrc`

<pre><code>gem install bundler
bundle install</code></pre>

+ Install the prepackaged theme: `rake install`

###Create Github page
* Go to your github page, and create a new repository. I suggest you make it in the format: `username.github.io`
* Make sure the default branch is set to master. 

* Back on the terminal: `rake setup_github_pages`

* When it prompts to add the link, make sure you add it in the form: `"http://username/username.github.io.git"`
* It should end by telling you that you can now deploy to: 'https://github.com/aribajahan/aribajahan.github.io.git' with `rake deploy`

* Then:
<pre><code>rake generate
rake deploy</code></pre>
* These two lines generates the packages and pushes it to the web. 

* Now commit it: 
<pre><code>git add .
git commit -am 'First commit'
git push origin source</code></pre>

* It may take some time for the site to go live if it's the first time. In the meantime, you can run it remote to preview by:
`rake preview`

* In your browser, launch: localhost:4000


