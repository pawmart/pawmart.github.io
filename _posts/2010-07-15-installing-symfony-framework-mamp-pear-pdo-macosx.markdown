---
layout: post
status: publish
published: true
title: Installing Symfony on Mac OSX with MAMP, PEAR and PDO
author: Pawel
author_login: admin
author_email: pawel@pawelmartuszewski.co.uk
author_url: http://www.pawelmartuszewski.co.uk
excerpt: How to install and configure Symfony on your Mac? The answer to this question
  is not obvious and various people suggest different approach. I recently have installed
  Symfony on my machine and decided to share a few tips how to achieve it. Things
  are not that complicated once you know what you are doing.
wordpress_id: 1834
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=1834
date: 2010-07-15 21:13:42.000000000 +01:00
categories:
- Tutorials
- PHP / MySQL
tags:
- PHP
- Symfony
comments:
- id: 415
  author: Fer
  author_email: blitzneo@hotmail.com
  author_url: ''
  date: '2010-07-22 08:39:24 +0100'
  date_gmt: '2010-07-22 07:39:24 +0100'
  content: "First, congrats for the article, I found it really interesting =)\r\nSo
    I decided to give it a try with my laptop (MacBook Pro 10.6.4), and repeating
    exactly the same steps you mentioned above. But I didn't get it properly installed.\r\nSometimes
    pear command is not recognized, sometimes I get \"permission denied\" message..
    Of course I'm not an expert.. =) Anyway I can see my symfony project created,
    using http://test, but with no images.\r\nI would like to repeat the whole process
    if possible, but dunno how to 'go back' to the initial point, this is to say,
    install MAMP, PEAR, Symfony (inside MAMP)... etc. I'm quite new to use Mac so
    maybe this is more difficult that I think.\r\nThanks for the post you made, really
    interesting guide."
- id: 416
  author: Pawel
  author_email: pawel@pawelmartuszewski.co.uk
  author_url: http://www.pawelmartuszewski.co.uk
  date: '2010-07-22 10:37:10 +0100'
  date_gmt: '2010-07-22 09:37:10 +0100'
  content: "Hi Fer,\r\n\r\nI had the same problem as you have now. In order to repeat
    everything once again I had to rollback my Mac a month back in time. If you will
    mess with aliases and environment variables it's hard to set things right again.
    \r\n\r\nTry to backup everything and install your system again... I know this
    sounds like a lot of work, but you will be sure that everything is set correctly.\r\n\r\nPS.
    Quick fix to see the images on your project is to simply copy /sf folder (located
    in your symfony directory) into your /web directory of your project.  Another
    way is to simply create an alias in your Virtual Host - pointing to this folder
    ( /sf ). \r\n\r\nHope this helps..."
- id: 424
  author: Fer
  author_email: blitzneo@hotmail.com
  author_url: ''
  date: '2010-07-24 06:48:54 +0100'
  date_gmt: '2010-07-24 05:48:54 +0100'
  content: "After reinstalling my system, I did follow this guide, but once again
    I didn't get the same results as you.\r\n\r\nInstalling MAMP, no problems, default
    ports, php 5.3.2 selected.\r\n\r\nInstalling PEAR.\r\n'As a shell command on your
    Terminal type:'\r\n\r\nI did that, but it's going to install in /private/var/root\r\nSo
    I guess I have to change it to /Users/Fer and then continue with installation
    (Am I wrong?)\r\nWhen installing PEAR, lots of 'errors' or 'warnings' like: xxxxxx
    function is deprecated in xxxxx, dunno if this is normal, or will affect in the
    future...\r\n\r\nSo, at the end of the installation I got this message:\r\n\r\n'Current
    include path: .:/usr/lib/php'\r\n'Configured directory: /Users/Fer/PEAR'\r\n'Current
    used php.ini (guess) : '\r\n\r\nAfter that, add the variables to the PATH with
    the export commands, once I did it, it says:\r\n'pear: command not found'\r\n\r\nBy
    the way, yesterday this step worked, but when I tried\r\n'sudo /Applications/MAMP/bin/php5.3/bin/peardev
    channel-discover pear.symfony-project.com'\r\nit also says 'command not found'\r\n\r\nSo
    I cannot get it working... Maybe I am missing some important step even before
    installing MAMP or something.\r\n\r\nThanks for your time and patience ^^"
- id: 425
  author: Pawel
  author_email: pawel@pawelmartuszewski.co.uk
  author_url: http://www.pawelmartuszewski.co.uk
  date: '2010-07-24 10:10:12 +0100'
  date_gmt: '2010-07-24 09:10:12 +0100'
  content: "Fer,\r\n\r\nHad exactly same issue with /private/var/root... The problem
    is when your MAC OSX installation is correct and 'clean', PEAR shouldn't wish
    to install itself in /private/var/root . When system is clean PEAR installation
    shouldn't give you any errors and 'function deprecated' alerts. And you shouldn't
    have to change your PEAR installation directory eather.\r\n\r\nAre you sure you
    have had 'clean' Leopard installed? Or you just reinstalled Leopard keeping old
    settings? This might be the problem...\r\n\r\nAbsolute nightmare with this Symfony
    installation isn't it? My guide worked for me... Once you got the solution that
    works for you, please come back and share it with us... Maybe we are missing something..."
- id: 426
  author: Fer
  author_email: blitzneo@hotmail.com
  author_url: ''
  date: '2010-07-24 10:15:00 +0100'
  date_gmt: '2010-07-24 09:15:00 +0100'
  content: "Should be 'super-clean' installation because I even formated the drive...
    So I'm lost right now. I can format again or restore, but I wanted it to work
    properly hehe =)\r\nI have the dvd here, so I can reinstall again I guess"
- id: 427
  author: Pawel
  author_email: pawel@pawelmartuszewski.co.uk
  author_url: http://www.pawelmartuszewski.co.uk
  date: '2010-07-24 10:25:15 +0100'
  date_gmt: '2010-07-24 09:25:15 +0100'
  content: "Hmm... maybe check MAMP version, restart servers before and after installing
    each component, type commands manually in your terminal... etc.\r\n\r\nPS. BTW
    my symfony installation took me 4 days lol... but once i figured out what need
    to be done, it took a minute...\r\n\r\nPS 2. The biggest problem with symfony
    is installation. Once you got everything installed it's just a breeze and joy..."
- id: 428
  author: web design
  author_email: seo.ilakiya@gmail.com
  author_url: http://www.vijayinfo.in
  date: '2010-07-24 10:33:25 +0100'
  date_gmt: '2010-07-24 09:33:25 +0100'
  content: Your blog is very nice... i like your blog ....
- id: 429
  author: Fer
  author_email: blitzneo@hotmail.com
  author_url: ''
  date: '2010-07-24 11:13:35 +0100'
  date_gmt: '2010-07-24 10:13:35 +0100'
  content: "MAMP installed successfully (version 1.9). Also checked that /Applications/MAMP/bin/php5.3/bin/peardev
    has the peardev thing in it. But still says command not found when I tried that
    step to both discover symfony channel and install it...\r\nI will continue trying
    later, now I go to have dinner... sometimes programming (or the steps before programming)
    are exhausting -_-\r\nThanks Pawel\r\n\r\nP.S.  After PEAR and MAMP are installed,
    should I change anything in any php.ini ? Maybe this is important :S"
- id: 430
  author: Pawel
  author_email: pawel@pawelmartuszewski.co.uk
  author_url: http://www.pawelmartuszewski.co.uk
  date: '2010-07-24 11:35:57 +0100'
  date_gmt: '2010-07-24 10:35:57 +0100'
  content: Some blogs point out that you have to provide a path to your PEAR directory...
    but I didn't have to modify anything there and it worked. Keep me updated Fer!
    I am interested in the outcome of your problem...
- id: 431
  author: Wordpress Themes
  author_email: ala234l@gawab.com
  author_url: http://genericwpthemes.com
  date: '2010-07-24 20:25:03 +0100'
  date_gmt: '2010-07-24 19:25:03 +0100'
  content: Gratefulness you on your information.
- id: 432
  author: Fer
  author_email: blitzneo@hotmail.com
  author_url: ''
  date: '2010-07-25 05:44:39 +0100'
  date_gmt: '2010-07-25 04:44:39 +0100'
  content: |-
    Well, finally made it Pawel =)
    So this is what I did.
    After installing MAMP, I just gave 755 permission to '/Applications/MAMP/bin/php5.3/bin/peardev'.
    Everything else was following your steps, so maybe it only was a permission issue with that folder. Now I am able to create project, to see all the images, and manage the databases =)

    Thanks for your help and tips!

    Now I will continue reading your SEO post ^^ It's an interesting one too!
- id: 433
  author: Pawel
  author_email: pawel@pawelmartuszewski.co.uk
  author_url: http://www.pawelmartuszewski.co.uk
  date: '2010-07-25 08:03:45 +0100'
  date_gmt: '2010-07-25 07:03:45 +0100'
  content: I am glad to hear that! Congrats! ;) Now time for Symfony Enjoyment!!
- id: 435
  author: online cna classes
  author_email: pausleal@simps.com
  author_url: http://www.cna-trainingclass.com/passing-the-cna-exam/
  date: '2010-07-30 03:01:13 +0100'
  date_gmt: '2010-07-30 02:01:13 +0100'
  content: this post is very usefull thx!
- id: 447
  author: Fat Loss for Idiots
  author_email: Denike@gmail.com
  author_url: http://ezinearticles.com/?Fat-Loss-4-Idiots---Best-Weight-Loss-Technique-With-a-Calorie-Shifting-Diet&amp;id=3594558
  date: '2010-08-11 17:24:02 +0100'
  date_gmt: '2010-08-11 16:24:02 +0100'
  content: Many people will agree with this article whoever many other's will disagree.
    Anyway I appreciate your hard work.
- id: 457
  author: Va Infotech
  author_email: vainfotechindia@gmail.com
  author_url: http://www.vainfotech.com
  date: '2010-09-09 15:04:51 +0100'
  date_gmt: '2010-09-09 14:04:51 +0100'
  content: "nice works\r\n\r\nthanks."
- id: 482
  author: giorgia
  author_email: Giorgia@dotPeak.com
  author_url: http://www.dotpeak.com
  date: '2010-10-15 14:23:59 +0100'
  date_gmt: '2010-10-15 13:23:59 +0100'
  content: nice tips, thanks a lot
- id: 486
  author: George
  author_email: wrightgd@gmail.com
  author_url: ''
  date: '2010-11-11 20:35:18 +0000'
  date_gmt: '2010-11-11 19:35:18 +0000'
  content: "sorry--basic question. still learning the ropes.\r\n\r\nwhen i try to
    install pear, typing php -q go-pear.php gives me php: command not found. Any ideas/suggestions?\r\n\r\nMAMP
    server was running when i tried this. thanks"
- id: 487
  author: Pawel
  author_email: pawel@pawelmartuszewski.co.uk
  author_url: http://www.pawelmartuszewski.co.uk
  date: '2010-11-11 22:51:10 +0000'
  date_gmt: '2010-11-11 21:51:10 +0000'
  content: i am guessing your pear installation did not succeed. try installing pear
    again...
- id: 499
  author: dg
  author_email: check_you_email@yahoo.com
  author_url: ''
  date: '2011-01-12 02:22:11 +0000'
  date_gmt: '2011-01-12 01:22:11 +0000'
  content: Had the EXACT same problem as Fer - the system is a brand new macbook so
    its a clean install.  I have updated to 10.6.6 so I'm not sure it thats a problem.
- id: 516
  author: thecakeisalie
  author_email: mr.2fast@gmail.com
  author_url: ''
  date: '2011-04-26 11:02:42 +0100'
  date_gmt: '2011-04-26 10:02:42 +0100'
  content: Spent half the day trying to get Symfony running on my laptop (10.6.7).
    I tried 2 other methods - regular mysql/apache with entropy php and XAMPP - and
    both resulted in a weird 500 error. All useless until I read your guide. Thanks!!!!!
---
<img width="154" height="154" src="http://www.pawelmartuszewski.co.uk/tuts/symfony_instlation/symfony_instalation.png" alt="Mac OSX Symfony installation" class="fl_lft thumb m_b_20" />How to install and configure Symfony on your Mac? The answer to this question is not obvious and various people suggest different approach. I recently have installed Symfony on my machine and decided to share a few tips how to achieve it. Things are not that complicated once you know what you are doing. Let's get strait to the point!
<div class="cl">&nbsp;</div>

We could always you symfony sandbox but in order to gain access the the shell commands we need to configure our localhost and install Symfony on our local environment.

In this short quide I am going to describe how to install MAMP Pro 1.9 on MAC OSX Snow Leopard 10.6.4 and then how to install PEAR and Symfony 1.4 Framework.

<h2>What is Symfony?</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

<a href="http://www.symfony-project.org/" title="Symfony">Symfony</a> is one of the most popular and powerful PHP (MVC based) Frameworks available out there. The biggest advantage of this framework is great <a href="http://www.symfony-project.org/doc/1_4/">documentation</a>, huge <a href="http://www.symfony-project.org/community">community</a> and millions of <a href="http://www.symfony-project.org/plugins/">plugins</a> to help you on your way. Symfony provides a complete solution to make your development processes faster and more efficient. On top of that, quality of your code becomes very high and further application expansion is easy.

<h2>Installing MAMP</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

First of all, install <a href="http://www.mamp.info/en/index.html">MAMP package</a>. If you have any problems with installing it follow this tutorial:  <a href="http://www.pawelmartuszewski.co.uk/web_tutorials/install-localhost-server-mamp/" title="How to install localhost server on your machine – Installing MAMP">How to install localhost server on your machine – Installing MAMP</a>. Make sure to setup your ports to default and select PHP version 5.

<h2>Installing PEAR</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

To install <a href="http://pear.php.net/">PEAR</a> we are going to use go-pear.php as an alternative way to install PEAR on the Mac. As a shell command on your Terminal type:

<div class="pre">
sudo su -<br />
curl http://pear.php.net/go-pear > go-pear.php<br />
php -q go-pear.php
</div>

Above commands installs PEAR on /Users/YOUR_USER_NAME/PEAR. Now we need to export this path and add it to the environment variable.

<div class="pre">
echo 'export PATH=/Users/YOUR_USER_NAME/PEAR:$PATH' >> ~/.bash_profile<br />
echo 'export PATH=/Users/YOUR_USER_NAME/bin:$PATH' >> ~/.bash_profile
</div>

By confirming all on screen alerts you should install your PEAR. Now the PEAR should be installed and configured. You can check that by typing 'pear' as your Terminal command.

<h2>Installing Symfony</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

Now, we are going to install Symfony. Restart your localhost and terminal first. We have MAMP environment installed on the machine so symfony is going to be installed directly from the MAMP folder. After the restart type:

<div class="pre">
cd <br />
sudo /Applications/MAMP/bin/php5.3/bin/peardev channel-discover pear.symfony-project.com<br />
sudo /Applications/MAMP/bin/php5.3/bin/peardev install symfony/symfony
</div>

Make sure your php path folder is correct. Go to your MAMP Application folder and check if 'peardev' is available under this path.

<h2>Further configuration</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

We are almost done. The last thing we need to do is to link php and mysql socket to be accessible globally. Otherwise we will be not able to access 'symfony' command and we will be not able to connect to the database from the shell commands and we will be getting PDO error.

<div class="hot"><img src="/tuts/symfony_instlation/pdo_error.png" alt="PDO error" /></div>

We can set all up by typing:

<div class="pre">
sudo ln -s /Applications/MAMP/bin/php5.3/bin/php php<br />
sudo ln -s /Applications/MAMP/tmp/mysql/mysql.sock /tmp/mysql.sock<br />
</div>

To gain access to mysql commands from the shell:

<div class="pre">
alias mysql=&acute;/Applications/MAMP/Library/bin/mysql&acute;<br />
alias mysqladmin=&acute;sudo /Applications/MAMP/Library/bin/mysqladmin&acute;<br />
alias mysqlstop=&acute;sudo /Applications/MAMP/Library/bin/mysqladmin -u root -p shutdown&acute;<br />
alias mysqlstart=&acute;sudo /Applications/MAMP/Library/bin/mysqld_safe&acute;
</div>
Again, make sure the MAMP paths match with yours.

Once all is done, you should be able to have access to 'pear' and 'symfony' from your Terminal.

Enjoy using this great PHP framework.
