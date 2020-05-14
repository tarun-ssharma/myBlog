---
title:  "Get started with hosting your site on github for free in 7 easy steps"
date:   2020-05-12
categories: jekyll github-pages
excerpt_separator: <!--more-->
---
Have something you want to share with the world? Follow these 7 quick and easy steps to get your site or blog up on github for free:
<!--more-->
<meta name="description" content="{{ post.excerpt }}">
1. (**Optional**) Getting a domain name:
	+ Can purchase domains online from sites like Bluehost, Namecheap etc.
	+ Useful if you want your own custom site url and don't want the *username.github.io* part which is attached inadvertently to every github pages site url.

2. Setting up a github repository to serve as the base for your github pages site:
	* Create a new repository with your github account, say *new_repo*
	* (**Optional but recommended**) [Create a new branch][create-branch] from the *master* branch for *new_repo*, named *gh-pages*. Make *gh-pages* [the default branch][default-branch] for this repo.
	* (**Optional**) Go to *Settings>Options>GitHub Pages* section on the repo page. There you'll see the *Source* branch (*gh-pages*) which will be used to built the github pages site associated with this repo. Also, you'll see the *Custom Domain* which you can set to your own custom subdomain, using [this guide][custom-domain-guide]. If you don't set any custom domain, your github pages site will be hosted at **https://*username*.github.io/*new_repo*/**

3. Clone *new_repo* to your local machine to include site related files.
4. Setup jekyll and its requirements:
	* Download [git bash][git-bash]
	* [Install jekyll using rubyinstaller][install-jekyll]
		* **Note:** While performing *ridk install* step, it asks for components which should be installed:
		![ruby installer message](/assets/images/ruby-installer-message.png)
		Make sure to select all three, one by one. If not, you might encounter the following error in later stages of installation: [Failed to build gem native extension][error]

5. Use jekyll to create site related files in your local *new_repo* folder:
	* Using git bash,navigate to your *new_repo* folder, and run the following command:
		```
		jekyll new . --force
		#=> adds new jekyll related files and folders within the current folder.
		```
	* Use *git status* command to see all the files added to the *new_repo* folder.This folder now has enough information for jekyll to create a website. Read [this doc][dir-str] to know more about the contents of this directory.
	* In your *_posts* directory, remove the existing file, and create a new one named *2020-05-12-github-pages-site-using-jekyll.markdown* with the following content and save it:
		```
		---
		title:  "My very first post"
		date:   2020-05-12
		---
		Hello World!
		```
	* Go ahead and build the jekyll site:
		```
		bundle exec jekyll serve --watch
		#=> This will start a local server to host the jekyll site based on new_repo.
		```
		* **Note:** Make sure you are within the root directory, and not within any of its subfolders, while executing this command.
	* Navigate to **localhost:4000** in a browser. This is where the jekyll site will be hosted locally.

6. Making the site public:
	* Once you are happy with the changes, commit and push the local code to remote repo *new_repo*. Make sure you are pushing to the *gh-pages* and not the *master* branch.
		```
		git add . #Adds all files to be staged to commit
		git commit -m 'My first commit' #Creates a commit
		git push -u origin gh-pages  #Pushes the local changes to remote branch
		```
	* Navigate to **https://*username*.github.io/*new_repo*/** or whatever custom domain you've set to check out your published github pages site.

7. [**Next Steps**] So now, we have a site, but its useless since we haven't added anything interesting. Jekyll gives you quite a lot of flexibility in that you can:
	* Add/modify/remove [posts][posts]
	* Add/modify/remove [pages][pages] in a similar way to posts
	* Use [plugins][plugins] for additional features like [enabling emojis][enbl-emoji]
	* Using pre-designed [themes][themes] to add visual flair like [this][theme-ex] one.


**Voila! Now go find some interesting topic to write about and get started!**

**To read in more detail about Jekyll, visit**:
* [Jekyll official documentation][jekyll-docs]
* [programminghistorian.org page on this topic][ph.org]

**To enhance your knowledge on Ruby Gems, Gemfile and Blunder**:
* [Ruby guides][ruby-guides]
* [Blunder official docs][blunder-docs]

**Check out the syntax of Kramdown markdown flavor used by jekyll at:**
* [Kramdown docs][kram-docs]


[create-branch]:https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-and-deleting-branches-within-your-repository
[default-branch]:https://help.github.com/en/github/administering-a-repository/setting-the-default-branch
[custom-domain-guide]: https://help.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site
[git-bash]: https://git-scm.com/download/win
[install-jekyll]: https://jekyllrb.com/docs/installation/windows/#installation-via-rubyinstaller
[error]: https://github.com/jekyll/jekyll/issues/7000
[dir-str]: https://jekyllrb.com/docs/structure/
[plugins]: https://jekyllrb.com/docs/plugins/
[enbl-emoji]: https://github.com/yihangho/emoji-for-jekyll
[themes]: https://jekyllrb.com/docs/themes/
[theme-ex]: https://github.com/mmistakes/minimal-mistakes
[posts]: https://jekyllrb.com/docs/posts/
[pages]: https://jekyllrb.com/docs/pages/
[ph.org]: https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages
[jekyll-docs]: https://jekyllrb.com/docs/
[ruby-guides]: https://guides.rubygems.org/
[blunder-docs]: https://bundler.io/docs.html
[kram-docs]: https://kramdown.gettalong.org/documentation.html
