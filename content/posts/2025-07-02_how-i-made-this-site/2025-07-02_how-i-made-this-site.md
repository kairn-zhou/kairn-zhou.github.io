---
title: How I Made This Site
date: 2025-07-02
categories:
  - hugo
draft: false
---

I created this website with GitHub, Visual Studio Code, Cloudflare, Hugo, and the *Today I Learned* theme for Hugo. 

<!--more-->

This will be an extremely detailed guide, to make things clear for people like me who are very new to the whole process. If that's you, I'm so glad you're here!

## Contents
[Why Make a Website?](./#why-make-a-website)\
[To CMS or Not To CMS](./#to-cms-or-not-to-cms)\
[Choosing a Theme](./#choosing-a-theme)\
[Prework](./#prework)\
	&nbsp; [Documentation](./#documentation)\
	&nbsp; [Tools](./#tools)\
[Making the Site](./#making-the-site)\
[Site Customization](./#site-customization)\
	&nbsp; [Writing Posts and Notes](./#writing-posts-and-notes)\
	&nbsp; [Changing Menu Items](./#changing-menu-items)\
	&nbsp; [Fonts and Colours](./#fonts-and-colours)\
	&nbsp; [Layouts](./#layouts)\
[Custom Domain](./#custom-domain)\
[That's It!](./#thats-it)

# Why Make a Website?
If you don't care too much about the *why*, and just want to see how I set up the *Today I Learned* Hugo theme, skip to [Prework](./#prework).

Otherwise, I'm here to tell you why I wanted to make a website, and why I think everyone should! 
- **Control over output**: Developed thoughts tend to need more space than a 4:5 rectangle or 280 characters. A personal website allows you to interact with the digital world on your terms. 
- **Cost**: We pay when we use for-profit platforms — be it with money, attention, or data. Though we often accept these costs for the services we receive, it feels freeing to have your own space on the outskirts of the internet, where you can do more of what you want without the constant feeling of strings attached. And you can do it all for 0 dollars!
- **Community**: I'm a fan of the [small internet](https://cheapskatesguide.org/articles/small-internet.html) — which has been gaining popularity in the last few years. I love building community offline, and this is one I've always wanted to join online. 
# To CMS or Not To CMS
So now I just had to make the site. But first, here are a few considerations I wanted to fulfill:
- I didn't want to [write everything in HTML](https://sharveshs.medium.com/how-to-create-a-simple-blog-website-using-html-and-css-only-1e2b264cb13a)
- I wanted to use a custom domain
- I didn't want to pay for anything other than the domain name renewal fees
- I wanted to have a lot of control over my work

With my first consideration, I realized I didn't want to hand-write my website like I had tried to in the past. Previously, I have tried hosting hand-written HTML sites on [Firebase](https://firebase.google.com/docs/hosting), which worked fine but was very time-consuming. For this reason, [neocities](https://neocities.org/) — which has been rising in popularity in recent years — also wouldn't work. 

With the rest of my considerations, I realized I didn't want use a [SaaS](https://www.reddit.com/r/SaaS/comments/16kxzyp/what_is_the_exact_definition_of_saas/) [CMS](https://themeisle.com/blog/what-is-a-content-management-system-cms/) platform (eg. Wordpress, Wix, Webflow) for a few reasons:
- Features including custom domains and unlimited storage were locked behind paid plans
- You have to log in to a browser in order to edit your site. This may not be a problem for most users, but I prefer having more direct access to my information. Related to this, SaaS CMS tend to have many [server-side dependencies](https://www.sitepoint.com/7-reasons-use-static-site-generator/#3fewerserversidedependencies)

With all that in mind, I decided that I would use Hugo, which I had already heard of thanks to my [friend](https://probablyalexzhu.github.io/blog/tutorial-how-i-made-this-website-and-you-can-too/). Hugo is a [Static Site Generator](https://www.sitepoint.com/7-reasons-use-static-site-generator/), which seems to fulfill all of my requirements. 
# Choosing a Theme
So now that we know we want to use Hugo, we should choose a theme! There are a [good few](https://themes.gohugo.io/) to choose from, and I have some {{< backlink "2025-07-02_my-favourite-hugo-themes" "personal favourites" >}}. For my site, I chose to use Michael Henriksen's *Today I Learned* theme for a few reasons:
- It's simple where it should be
- The extra features it does have are actually useful to me: I really love the graph view. I've been a huge fan of the Obsidian graph embed ever since I saw how Sebastian Gorton Kalvik uses it in [his personal site](https://aaa.pm/notes/digital-garden/). I also like how notes and posts are separate — notes makes me feel like I have permission to release even my unpolished thoughts. 
- It has built-in blocking of AI web crawlers: I do not want my work being used as AI training data.

If you want to use a different Hugo theme, this guide may not be the most helpful, as different themes will handle things a bit differently. 
# Prework
## Documentation
If you look through forum posts from beginners seeking advice, you will often see responses urging them to "read the documentation". Documentation is written to be helpful and read, but it tends to assume that readers have the basic understanding of software to perform routine operations, when this is sometimes not the case (it sure wasn't the case for myself).\
Anyway, here is some relevant information in case you do want to do some independent reading first (I will also link them throughout the guide when relevant):
- [What is Git?](https://probablyalexzhu.github.io/blog/lightning-speed-tutorial-git-and-github/)
- [Hugo quick start](https://gohugo.io/getting-started/quick-start/)
- [Today I Learned Hugo theme information](https://michenriksen.com/til-example-site/)
## Tools
You need to **make an account** on:
- [GitHub](https://github.com/signup)
- [Cloudflare](https://dash.cloudflare.com/sign-up) (optional. do this if you want to use a custom domain for your website)

You need to **download**:
- [Node.js](https://nodejs.org/en/download/current) (scroll to the bottom and download the Windows Installer, and run it)
- [Git](https://git-scm.com/)
- [Go](https://go.dev/)
- [Hugo](https://gohugo.io/installation/), using a [package manager (these are for Windows)](https://gohugo.io/installation/windows/#package-managers)
- [Visual Studio Code](https://code.visualstudio.com/Download) (you'll want to sign in with your GitHub account)
# Making the Site
1. On GitHub, [create a repository](https://pages.github.com/) called "<your_username>.github.io".
	- Make it **public** (a paid plan is required to host a site on GitHub pages from a private repository)
	- **Don't** add a README, .gitignore, or license (we will do this later in VSCode in order to simplify the process, avoiding having to git pull)
	- You should now see some instructions. We'll follow those later
2. In your computer's file explorer, navigate to where you want to make your site, and **create a folder** (you can name it anything you want). I made a folder called "kairn-site" in my Desktop folder.
3. Open that folder in Visual Studio Code. This is called your "root folder". Everything needed for our website will be contained here. In the Visual Studio Code terminal, type:
``` terminal
hugo new site .
```

4. Manually, we will do a few things:
	- Add a **.gitignore** file into the root folder. You can copy the contents from [here](https://github.com/michenriksen/hugo-theme-til/blob/main/.gitignore).
	- You can also add a **README.md** file in the root folder. This is where you can write information about your website.
	- Copy the **package.json**, and **package-lock.json** files from the [site example repository](https://github.com/michenriksen/til-example-site/tree/main) into your root folder. Also copy the contents of the **/content folder** into your empty content folder.
5. Following the [theme docs](https://michenriksen.com/til-example-site/posts/installation/), we will now initialize the site as a Hugo module, and **add the theme as a module** as well. Hugo's [quickstart](https://gohugo.io/getting-started/quick-start/) guide recommends adding the theme as a submodule instead, but there are a few [benefits](https://www.adamormsby.com/posts/012-hugo-modules/) to our method (which I honestly do not fully understand myself).
``` terminal
hugo mod init github.com/<your_username>/<your_username>.github.io
hugo mod get github.com/michenriksen/hugo-theme-til
```
7. Continuing with the theme docs, we can **install vis-network**, which is used to render the graphs.
``` terminal
npm install vis-network
```
8. Continuing with the theme docs, replace the contents of your current hugo.toml with [this](https://michenriksen.com/til-example-site/posts/installation/#site-configuration). Remember to **change the baseURL** to "https://<your_username>.github.io".
9. Now we will set up the **building and deployment** of our site to GitHub Pages. This will make our site appear when we visit the link, "https://<your_username>.github.io", after the site is officially published. Follow these [docs](https://gohugo.io/host-and-deploy/host-on-github-pages/) from step 3 to 7 (step 5 is optional).
10. At this point, we can type "**hugo serve**" in the terminal, and follow the link to view our website locally. It's not published yet! This is just a preview that allows you to see what your site will look like when it is published. 
11. We can now **publish our site**. We will initialize our local Git repository, commit our files in it, and then push everything to our remote GitHub repository. To do this, type the following in the terminal (you will notice that it is similar to the instructions at the top of your new empty GitHub repository page):
``` terminal
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/kairn-zhou/kairn-zhou.github.io.git
git push -u origin main

```
12. Celebrate! Your site should be up at "https://<your_username>.github.io" after a few seconds. You can [watch the progress](https://gohugo.io/host-and-deploy/host-on-github-pages/#step-9). 
# Site Customization
There are more [configuration options](https://michenriksen.com/til-example-site/posts/configuration/) in your hugo.toml file.
## Writing Posts and Notes
Every page of content we create needs **frontmatter**. This is what frontmatter for posts and notes looks like:
``` markdown
---
title: Post Title
date: 2025-07-01
categories: 
- one-category
- another-category
draft: false
---
```

Then, you can write the content of the post underneath. This follows traditional [markdown](https://daringfireball.net/projects/markdown/) syntax. But our theme has a few [unique features](https://michenriksen.com/til-example-site/posts/shortcodes/) that you can add with **shortcodes**.
## Changing Menu Items
If you want to add or change menu items (defaults are Notes, Posts, Graph), you must make changes to the **[menus]** section in your hugo.toml file. Follow the formatting conventions to add or remove a menu section. 

To make the actual menu page, add a new .md file in the /content folder, and make sure the "**pageRef**" in the hugo.toml menu file refers to the **same name**. You don't need to add a date or categories in the frontmatter of these pages.
## Fonts and Colours
To be honest I cannot for the life of me figure out how to change these.
## Layouts
If you want to change the layout of a page on your site, look in the /layouts folder of the [theme docs](https://github.com/michenriksen/hugo-theme-til) repository.  If you copy any part of this folder and file structure into your own /layouts folder and make edits to the HTML, the site will be generated with your layout instead of the default theme layout.
# Custom Domain
If you want to be able to visit your site from a custom domain, you need to buy a domain and manage the DNS records for it. You can [find a good deal](https://tld-list.com/) for your domain with any registrar (including [Cloudflare's registrar](https://domains.cloudflare.com/)) and use Cloudflare as your [DNS provider and record manager](https://developers.cloudflare.com/dns/zone-setups/full-setup/setup/). Most registrars will provide the latter service for managing your domain's DNS records, but I chose to use Cloudflare because my friend recommended it to me on account of its high standard security features. After 60 days, you can [transfer your domain](https://developers.cloudflare.com/registrar/get-started/transfer-domain-to-cloudflare/) to Cloudflare if you wish.

Once you own a domain, navigate from your GitHub repository to Settings>Code and automation>Pages. Here we will add our custom domain (I added kairnzhou.com). For now, the DNS check will fail because we have not added the correct DNS records in Cloudflare.

In Cloudflare's DNS record configuration, we will create some DNS records to point our domain name to our new GitHub site (i.e. your domain name will redirect to your website). Create:
- 4 A records ([follow step 5](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site). Adding the AAAA records is optional.)
- 1 CNAME record (mine has name: www, target: kairnzhou.com)
- If you wish, you can also verify your domain by clicking your profile icon in the top right>Code, planning, and automation>Pages. Add your domain and create 1 TXT record in Cloudflare following the instructions.

Now, when you go back to the DNS check, it should work. You can check the "Enforce HTTPS" box if you wish. 

Note that some actions may not work immediately because DNS takes some time to propagate (minutes to 72 hours sometimes). If you think you're doing everything right, but some things still aren't working, you might just need to wait a while. 
# That's It!
That's it! Congratulations, you have website with posts now. Thanks for following along!
___
**Disclaimer**: This is mainly just a reminder for myself as to how I created the site. I am new to all of this and have probably communicated some information incorrectly, but this is what worked for me. Don't hesitate to [reach out](/about) with any feedback!