---
layout: post
status: publish
published: true
title: How to get the current page url
author: Pawel
author_login: admin
author_email: pawel@pawelmartuszewski.co.uk
author_url: http://www.pawelmartuszewski.co.uk
excerpt: Sometimes, there is a need to get the current url to be used within the php
  code. This is very useful function for social media shearing, as you might want
  to sent a current page url to be bookmarked or shared with others. You can easily
  echo your page url using a very simple php function.
wordpress_id: 847
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=847
date: 2009-11-14 22:41:00.000000000 +00:00
categories:
- Design
- Code
- Articles
tags:
- PHP
comments:
- id: 65
  author: Allen Patterson
  author_email: allenpatterson@mac.com
  author_url: http://www.aptune.com
  date: '2009-11-15 21:21:00 +0000'
  date_gmt: '2009-11-15 20:21:00 +0000'
  content: "It is a breath of fresh air to come to a website that has meaning content.
    Thank you for the follow on Twitter and I will be using your website quite often
    while i study PHP. I am just a beginner in PHP but hope to convert my website
    and control my tutorials in my own data base.\r\nSincerely,\r\nAllen Patterson\r\nCEO
    \r\nhttp://www.aptune.com\r\nI just added you to my personal bookmarks!"
- id: 66
  author: Pawel
  author_email: pawel@pawelmartuszewski.co.uk
  author_url: http://www.pawelmartuszewski.co.uk
  date: '2009-11-15 21:41:50 +0000'
  date_gmt: '2009-11-15 20:41:50 +0000'
  content: "Thanks for your comment.\r\n\r\nFeel free to request a tutorial if you
    stuck on something. Use my contact form for that. I will be more then happy to
    help if I can.\r\n\r\nHave a great coding!"
---
<img class="fl_lft thumb m_b_20" width="154" height="154" title="current page url" alt="current page url" src="http://www.pawelmartuszewski.co.uk/artls/cur_page/cur_page.png"/>Sometimes, there is a need to get the <strong>current url</strong> to be used within the php code. This is very useful function for <strong>social media shearing</strong>, as you might want to sent a <strong>current page url</strong> to be bookmarked or shared with others. You can easily <strong>echo your page url</strong> using a very simple php function.
<div class="cl"></div>
<h2>Add the following function</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<div class="pre">
&lt;?php<br />
  function CurrentURL()<br />
  {<br />
  $pageURL = $_SERVER['HTTPS'] == 'on' ? 'https://' : 'http://';<br />
  $pageURL .= $_SERVER['SERVER_PORT'] != '80' ? $_SERVER[&quot;SERVER_NAME&quot;].&quot;:&quot;.$_SERVER[&quot;SERVER_PORT&quot;].$_SERVER[&quot;REQUEST_URI&quot;] : $_SERVER['SERVER_NAME'] . $_SERVER['REQUEST_URI'];<br />
  return $pageURL;<br />
  }<br />
  ?&gt;
</div>
<h2>Echo this function to get the current page URL</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<div class="pre">
&lt;?php  echo CurrentURL(); ?&gt;
</div>
<p>This is it. I hope you like it. Any comments welcome. Enjoy!</p>
