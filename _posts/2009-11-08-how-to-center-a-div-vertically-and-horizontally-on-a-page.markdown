---
layout: post
status: publish
published: true
title: How to center a div vertically and horizontally on a page
author: Pawel
author_login: admin
author_email: pawel@pawelmartuszewski.co.uk
author_url: http://www.pawelmartuszewski.co.uk
excerpt: I came across many young designers asking how to center an element on the
  website and not using the table. Using table layout is was very easy but not so
  obvious when we use divs.
wordpress_id: 1127
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=1127
date: 2009-11-08 01:30:07.000000000 +00:00
categories:
- Tutorials
- CSS Tutorials
tags: []
comments:
- id: 191
  author: Dan
  author_email: dan@wp.pl
  author_url: ''
  date: '2010-01-10 22:23:38 +0000'
  date_gmt: '2010-01-10 21:23:38 +0000'
  content: Great! It works, thanks!
---
<p><img class="fl_lft thumb m_b_20" width="154" height="154" title="center a div vertically and horizontally" alt="center a div vertically and horizontally" src="http://www.pawelmartuszewski.co.uk/artls/center_div/center_positioning.jpg"/>I came across many young designers asking how to centre an element on the website and not using the table. Using table layout is was very easy but not so obvious when we use divs. I am not going to go into details why divs not tables because it is not the intention of this article.
<a href="http://www.pawelmartuszewski.co.uk/artls/center_div/index.html" target="_blank" class="btn btn_demo"></a><a href="http://www.pawelmartuszewski.co.uk/artls/center_div/center_div.zip" class="btn btn_source"></a></p>
<div class="space">&nbsp;</div>
<p class="pt">HTML code</p>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<div class="pre">
&lt;body&gt;<br />
&lt;div id=&quot;out&quot;&gt;<br />
&lt;div id=&quot;cnt&quot;&gt;<br />
&lt;h1&gt;Header&lt;/h1&gt;<br />
&lt;p&gt;Content of the centered element&hellip;&lt;/p&gt;<br />
&lt;/div&gt;<br />
&lt;/div&gt;<br />
&lt;/body&gt;
</div>


<p>This is really basic html. To centre the element we need 2 divs. Our #out div is the outer element that we will be referring to, in order to position our #cnt div (our content element).</p>
<p class="pt">CSS code</p>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<div class="pre">
#out {
	position: absolute;
	top: 50%;
	left: 0px;
	width: 100%;
	height: 1px;
	overflow: visible;
}
#cnt {
	width: 400px;
	height: 80px;
	margin-left: -200px;  /* width of the #cnt / 2 */
	position: absolute;
	top: -40px;          /* height of the #cnt / 2 */
	left: 50%;
	text-align:center;
}
</div>

<p>The outer div is positioned 50% from the top, it means half way down the page.</p>
<p>Next we style our #cnt div (content) giving a negative top position which is half of the actual height. This is in order to place it exactly on the middle. Additionally we place it half way horizontally (left:50%) and have a negative left margin which is half of the actual width. The rest should be easy to understand.</p>

<p class="pt">Conclusion</p>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<p>I have tested it on Firefox 2 and 3 then on Opera 9, Safari 3 and IE 4, 5, 6, 7. Please let me know if you found it not working on your browser.</p>
<p>This is nothing new but might be helpful to someone. Don&acute;t forget to leave a comment.</p>
