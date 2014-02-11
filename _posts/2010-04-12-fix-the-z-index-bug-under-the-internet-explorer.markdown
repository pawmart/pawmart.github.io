---
layout: post
status: publish
published: true
title: Fix the z-index bug under the Internet Explorer
author: Pawel
author_login: admin
author_email: pawel@pawelmartuszewski.co.uk
author_url: http://www.pawelmartuszewski.co.uk
excerpt: Positioning the HTML elements using relative or absolute positioning, can
  bring a problem with z-index positioning especially  under the Internet Explorer
  (beloved browser lol). This can be extremely frustrating problem, but easy to fix.
wordpress_id: 1699
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=1699
date: 2010-04-12 18:48:33.000000000 +01:00
categories:
- Tutorials
- CSS Tutorials
tags:
- Fun
- CSS
- debug
comments:
- id: 390
  author: Keith
  author_email: keithspencer10@gmail.com
  author_url: ''
  date: '2010-06-18 10:25:14 +0100'
  date_gmt: '2010-06-18 09:25:14 +0100'
  content: Very helpful and works. Thanks!!
- id: 446
  author: Simon
  author_email: smck102617@hotmail.co.uk
  author_url: ''
  date: '2010-08-11 11:24:35 +0100'
  date_gmt: '2010-08-11 10:24:35 +0100'
  content: Thanks a million for this, got me out of a sticky situation!
- id: 512
  author: Sangeeta
  author_email: sangee_arshi@yahoo.co.in
  author_url: ''
  date: '2011-04-05 18:29:01 +0100'
  date_gmt: '2011-04-05 17:29:01 +0100'
  content: thanks a lot --it is working -- ie6 is really nonsense but this post make
    it much in hand--thanks a lot
---
<img class="fl_lft thumb m_b_20" width="154" height="154" alt="Fix the z-index bug under the Internet Explorer" src="http://www.pawelmartuszewski.co.uk/tuts/z_index/z-index.jpg" />Positioning the HTML elements using relative or absolute positioning, can bring a problem with z-index positioning especially  under the Internet Explorer (beloved browser lol). This can be extremely frustrating problem and I have been avoiding relative and absolute positioning, transforming my designs into the HTML. In fact, it is easy to fix it. The problem is easy to solve when you understand how Internet Explorer reads relative or absolute positioning. 

<div class="cl">&nbsp;</div>
<h2>Problem</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

Let's bring up the example to work with. Navigation with drop-down menu and content element positioned absolutely (content images). Under the Internet Explorer z-index is somehow ignored and it seem not possible to put our content images above the drop-down navigation.

<div class="hot"><img src="http://www.pawelmartuszewski.co.uk/tuts/z_index/before.jpg" alt="Fix z-index bug under the Internet Explorer" /></div>

Drop-down menu element is obviously positioned absolutely where the relative element is our main navigation container. So the structure reads:
<div class="pre">
<span class="b">&lt;!-- relative positioning on main navigation container --&gt;</span><br />
&lt;ul id=&quot;main_nav&quot; style=&quot;position:relative&quot;&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Home&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;About&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;<br />
<span class="b">&lt;!-- absolute positioning on drop-down navigation --&gt;</span><br />
&lt;ul id=&quot;drop_down_nav&quot; style=&quot;position:absolute&quot;&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Sub-nav&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Sub-nav&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Sub-nav&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Sub-nav&lt;/a&gt;&lt;/li&gt;<br />
&lt;/ul&gt;<br />
&lt;/li&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Products&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;
</div>

All you have to do is to put higher z-index on the parent (or grandparent if any) element of the navigation.

<div class="pre">
<span class="b">&lt;!-- relative positioning on main navigation container --&gt;</span><br />
&lt;ul id=&quot;main_nav&quot; style=&quot;position:relative;z-index:5000&quot;&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Home&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;About&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;<br />
<span class="b">&lt;!-- absolute positioning on drop-down navigation --&gt;</span><br />
&lt;ul id=&quot;drop_down_nav&quot; style=&quot;position:absolute;z-index:2000&quot;&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Sub-nav&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Sub-nav&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Sub-nav&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Sub-nav&lt;/a&gt;&lt;/li&gt;<br />
&lt;/ul&gt;<br />
&lt;/li&gt;<br />
&lt;li&gt;&lt;a href=&quot;#&quot;&gt;Products&lt;/a&gt;&lt;/li&gt;<br />
&lt;li&gt;
</div>

The works because IE doesn’t allow elements to have a higher z-index than their parent (grandparents) element.

<p class="b">The issue is that when you give a relative positioning to a container (our main navigation), it restarts the z-indexing inside of it at 0, and the global-level z-index of everything inside the container becomes the same as the parent.</p>

You need to put the higher z-index on the top most relatively positioned element. Don’t just put the higher z-index on the parent element, put it on the first parent that is positioned relatively.

<h2>Solved solution</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

<div class="hot"><img src="http://www.pawelmartuszewski.co.uk/tuts/z_index/after.jpg" alt="Fix z-index bug under the Internet Explorer" /></div>

As you can see, now our drop-down navigation appear in front of the content images. 

<h2>Javascript approach</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

Alternatively we can use jQuery solution. The code will start with a z-index of 1000, and decrement the z-index for each DIV element of the page.

<div class="pre">
if(Browser.Engine.trident){
	var zIndexNumber = 1000;
	$$('div').each(function(el,i){
		el.setStyle('z-index',zIndexNumber);
		zIndexNumber -= 10;
	});
};
</div>

I hope you enjoyed.
