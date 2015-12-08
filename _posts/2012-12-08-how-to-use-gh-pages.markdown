---
layout: post
title: "How to host an existing website on GitHub Pages"
date: 2015-12-08 21:00:00
categories:
 - gci
 - foss
 - github
---

GitHub Pages is a great way to host a static (read: no server-side component, just HTML, CSS and JavaScript)
for free. It's available to anyone with a GitHub account. In this post I'll explain how to set up a static site on there. Trust me, it's really easy.

Now, this post assumes that you have a GitHub account, if you don't, you can create one for free at <a href="https://github.com">github.com</a>. I'll
also assume that you already have a website made, if not, there are countless tutorials around on how to make one, Google is your friend.
Finally, I'll assume that you've got the `git` version control system installed on your computer.

## Setting Up GitHub

To host our site on GitHub, we'll first need to create a repository for it. If you've used `git` before, you'll already
know what a repository is, and a GitHub repo is no different.

On the top-right corner of the screen click the plus icon and select `New Repository`, as shown in the screenshot below.

![Screenshot of the GitHub homepage, with the New Repository link highlighted.]({{ site.url }}/assets/gh-pages/Capture1.png)

You get these options:

![Form that shows when New Repository link followed]({{ site.url }}/assets/gh-pages/Capture2.png)

Here's what to do there:

|Field|Explanation|
|---|---|
|Repository Name|What you want your site to be called|
|Description|Will be shown to people who look at your repository, whatever you want|
|Public/Private|Unless you have a paid-for GitHub account you won't be able to choose Private, so go Public|
|Initialize this repository with a README|Not necessary (contrary to what they say), so leave unchecked|
|Add .gitignore|Leave as None|
|Add a license|Choose a license for your site's code (beyond the scope of this post, <a href="http://choosealicense.com/">here</a> is a good explanation), leave as none if in doubt.|

Once you've created your repo, you'll see this screen:

![Screenshot of our new repo!]({{ site.url }}/assets/gh-pages/Capture3.png)

## Creating a local repository

Now, we need to create a `git` repo for our site on our local computer. If your site is already in a repo, skip this step.

Open a command line however you do on your operating system and `cd` to where your site's files are. Then, type these commands (don't type the `$` character or the comments (the bits after `#`)):

{%highlight bash %}

$ git init # Create a repository
Initialized empty Git repository in C:/Users/Marks Polakos/IdeaProjects/potato/.git/

$ git add . # Add all the files in this folder to our repo, don't forget the full stop!

$ git commit -m "Initial commit" # Commit our changes, save them to the repo. Write something meaningful in place of 'Initial commit' (do as I say, not as I do!)

{% endhighlight %}

## Linking our local repository to GitHub

Now comes the clever bit. Go back to the GitHub website and copy this URL:

![Close up of the repo's URL]({{ site.url }}/assets/gh-pages/Capture4.png)

Now, in your command line. type:

{%highlight bash %}

$ git remote add origin https://github.com/marksomnian/turbulent-octo-woof.git # Save that URL as a link to a remote repository (on GitHub)

{% endhighlight %}

What you've just done is told `git` on your computer where to upload all your code when you tell it to. In `git` terminology,
 this is called a *remote*. You didn't have to call it `origin`, by the way, you could have just as well called it
  `HeyLookThisIsWhereMySiteIsGuys`, but it's an accepted convention to call the main remote `origin`.

## Uploading our site to GitHub

Now comes the *really* clever bit:

{%highlight bash %}

$ git checkout -b gh-pages # Create a new branch called gh-pages and switch to it
Switched to a new branch 'gh-pages'

$ git push origin gh-pages # Upload our new gh-pages branch to the origin server (GitHub), on a branch called gh-pages
Counting objects: 38, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (38/38), done.
Writing objects: 100% (38/38), 490.84 KiB | 0 bytes/s, done.
Total 38 (delta 4), reused 0 (delta 0)
To https://github.com/marksomnian/turbulent-octo-woof.git
 * [new branch]      gh-pages -> gh-pages

{% endhighlight %}

This bears some explanation. With a branch called `gh-pages`, you're basically telling GitHub
 **"Hey GitHub, here's the code for my website, host it for me please!"** And, if everything goes well, GitHub obliges.

## Did it work?

And now, if everything goes according to plan, go to `http://yourusername.github.io/yourreponame`, substituting `yourusername` and `yourreponame`. And hey presto!

![Hey presto!]({{ site.url }}/assets/gh-pages/Capture5.png)

Now, the reason my address bar says `markspolakovs.me` instead of `marksomnian.github.io` is because I've set up my GitHub pages with my custom domain name, `markspolakovs.me`.
For you it should be `yourusername.github.io`.

I hope this post has helped you take your first website up to the CLOOOOUD! Leave any comments in the, well, comments section down below, and until next time, ***stay coding***.