---
layout: post
status: publish
published: true
title: How to implement TweetMeme Button on your website
author: Pawel
author_login: admin
author_email: pawel@pawelmartuszewski.co.uk
author_url: http://www.pawelmartuszewski.co.uk
excerpt: In this very short article I am going to show you how to implement a TweetMeme
  badge to your website. This is a great way to encourage your visitors to re-tweet
  your story. You might want to implement it to your WordPress or non WordPress website.  I'll
  show both ways of getting a TweetMeme badge.
wordpress_id: 834
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=834
date: 2009-11-14 22:43:16.000000000 +00:00
categories:
- Design
- Code
- Articles
tags:
- Wordpress
- PHP
- Twitter
comments:
- id: 62
  author: LeviD
  author_email: mcvippa@hotmail.com
  author_url: ''
  date: '2009-11-15 17:58:13 +0000'
  date_gmt: '2009-11-15 16:58:13 +0000'
  content: Very nice toturial its realy important!
- id: 68
  author: Seb
  author_email: mail@mail.com
  author_url: http://www.sebastiansulinski.co.uk
  date: '2009-11-20 17:31:18 +0000'
  date_gmt: '2009-11-20 16:31:18 +0000'
  content: Great article - keep up the good work!
- id: 99
  author: Bob
  author_email: rnewman2@chi.ac.uk
  author_url: ''
  date: '2009-12-02 23:44:20 +0000'
  date_gmt: '2009-12-02 22:44:20 +0000'
  content: Really useful information! and it works!!!
---
<img class="fl_lft thumb m_b_20" width="154" height="154" title="retweet button implementation" alt="re-tweet button implementation" src="http://www.pawelmartuszewski.co.uk/artls/retweet/retweet.png"/>In this very short article I am going to show you how to implement a TweetMeme badge to your website. This is a great way to encourage your visitors to re-tweet your story. You might want to implement it to your WordPress or non WordPress website.  I'll show both ways of getting a TweetMeme badge.
<div class="cl"></div>
<h2>What is TweetMeme?</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<strong>TweetMeme</strong> is a service that puts all the popular links on Twitter together in one place to determine which links are popular. Then it takes these links and categorises them in order to filter out what you are interested in. You can find out more on <a href="http://tweetmeme.com/" title="TweetMeme Website" target="_blank">TweetMeme</a>.
<h2>TweetMeme Button on your post or page</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
The button provides a URL and the title of the story or page. Every single link that is posted on Twitter adds one to the tweet count of the story. So this TweetMeme button (badge) can be a very good idea to r<strong>emind to your visitors to re-tweet your story</strong>. TweetMeme website describes an implementation processes but they did&acute;t work for me, so I decided to write about custom implementation. So, let&acute;s crack on!
<h2>TweetMeme badge php function</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
You will need to include this php function at the end of your <strong>functions.php</strong> file. If you are not using a WordPress and don't have a functions.php file, just simply paste it as a php code on a page before any header request.
<div class="pre">
&lt;?php<br />
function tweetmeme(){<br />
?&gt;<br />
&lt;div style=&quot;float: right; margin: 5px 10px 5px 0px;&quot;&gt;<br />
&lt;script type=&quot;text/javascript&quot;&gt;<br />
tweetmeme_url = '&lt;?php the_permalink(); ?&gt;';<br />
&lt;/script&gt;<br />
&lt;script type=&quot;text/javascript&quot; src=&quot;http://tweetmeme.com/i/scripts/button.js&quot;&gt;&lt;/script&gt;<br />
&lt;/div&gt;<br />
&lt;?php<br />
}<br />
?&gt;
</div>
<p>If you are not using WordPress, you need to get the current page url and replace <?php the_permalink(); ?> with it. Read my post on <a href="http://www.pawelmartuszewski.co.uk/web-design/how-to-get-the-current-page-url/" title="How to get the current page url">How to get the current page url</a>.</p>
<p>If you want to add your twitter id to visitors re-tweet, next to the url, you need to add one more line just after the tweetmeme_url in our code.</p>
<div class="pre">
tweetmeme_source = 'pmdesignweb'; /*this is your twitter name */<br />
</div>
<h2>Getting badge displayed on your page</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
Now you have got a few choices depending on what you want to do. You might want to show the badges on every single post, if this is the case just locate your posts template (<strong>index.php</strong> or <strong>single.php</strong> for WordPress) and echo the function just before the <strong><?php the_content(); ?></strong> or <strong><?php the_excerpt(); ?></strong>. If your website is non WordPress just <strong>echo this function</strong> where you want your badge to be displayed.
<div class="pre">
&lt;?php echo tweetmeme(); ?&gt;
</div>
<p>If you want to display in on some of the posts only and you would like to have a full control on what post the badge is displayed you might want to you <strong>custom fields</strong> on WordPress. If this is the case, instead of echoing the function we can check if the custom field was defined and if it was then echo the function. See the code below:</p>
<div class="pre">
&lt;?php <br />
  $check_sm = get_post_meta($post-&gt;ID, 'tweetmeme', $single = true);<br />
  if($check_sm != '')<br />
  tweetmeme();<br />
?&gt;
</div>
<p>Now create a custom field on the post called TweetMeme and set the value to true. The badge will only be displayed on posts containing this custom field. Enjoy!</p>
