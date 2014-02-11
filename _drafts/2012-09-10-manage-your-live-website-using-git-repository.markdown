---
layout: post
status: publish
published: true
title: Manage your live website using git repository
author: Pawel
author_login: admin
author_email: pawel@pawelmartuszewski.co.uk
author_url: http://www.pawelmartuszewski.co.uk
wordpress_id: 2105
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=2105
date: 2012-09-10 21:36:20.000000000 +01:00
categories:
- Code
- Articles
tags:
- Git
- Subversion
comments: []
---
<img src="http://www.pawelmartuszewski.co.uk/wp-content/uploads/git.jpg" alt="git" title="git" width="154" height="154" class="fl_lft thumb m_b_20" style="border:none !important;"  />FTP connections (lets face it) are buggy / hard to manage, slow and not version controlled which courses serous problems when ftp fails (overwriting the file with failure). Version control in place allows us to manage our files in more efficient way. This quick post will show how to set a local git repository and push it to remote server (live).
<div class="cl"></div>
<h2>The local repository</h2>
<div class="dev"><div class="dev_in"></div></div>

First of all we need to set up our local git repository if we didn't already.
<pre>
$ mkdir siteFolder && cd siteFolder
$ git init
Initialized empty Git repository in /home/dmd/siteFolder/.git/
$ echo 'Hello, world!' > index.html
$ git add index.html
$ git commit -q -m "This is my first commit."
</pre>

<h2>The remote repository</h2>
<div class="dev"><div class="dev_in"></div></div>

Having local repo in place, now we need to have our remote equivalent (the place where we wish to push our changes. The best place to set up is outside our public_html on our hosting account.

<pre>
$ mkdir siteFolder.git && cd siteFolder.git
$ git init --bare
Initialized empty Git repository in /home/dmd/siteFolder.git/
</pre>

Now we need to tell our repo that our directory is 'public_html'.

<pre>
$ mkdir /home/dmd/siteFolder/public_html
$ cat > hooks/post-receive
#!/bin/sh
GIT_WORK_TREE=/home/dmd/siteFolder/public_html git checkout -f
$ chmod +x hooks/post-receive
</pre>

The above will ensure all our changes are pushed to 'public_html' directory our our server.


<h2>First remote push!</h2>
<div class="dev"><div class="dev_in"></div></div>

<pre>
$ git remote add website ssh://server.example.org/home/dmd/siteFolder.git
$ git push website +master:refs/heads/master
</pre>

<h2>Updating our website</h2>

All we have to do is to:

<pre>
$ git push website
</pre>

Or you can set your default push and pull branch by:

<pre>
$ git branch --set-upstream master website/master
</pre>

So, you can do 'git push' or 'git pull'.

<h2>Permissions</h2>

To sort out permissions problem you need to add chown to your post-receive file located at /hooks/post-receive

<pre>
chown user:group -R public_html/
</pre>

Hope this helps.
