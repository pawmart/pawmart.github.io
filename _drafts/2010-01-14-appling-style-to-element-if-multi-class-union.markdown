---
layout: post
status: publish
published: true
title: Applying style to an element only if multi-class union exist
author: Pawel
author_login: admin
author_email: pawel@pawelmartuszewski.co.uk
author_url: http://www.pawelmartuszewski.co.uk
excerpt: Using CSS, you can apply multiple styles to one HTML element. This is obvious
  and helps to keep our HTML and CSS clean and redundant. What happens if we want
  to style the element differently ONLY if two different classes applied?
wordpress_id: 1246
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=1246
date: 2010-01-14 23:48:28.000000000 +00:00
categories:
- Tutorials
- CSS Tutorials
tags:
- Fun
comments:
- id: 207
  author: Dan
  author_email: dan@wp.pl
  author_url: ''
  date: '2010-01-17 21:07:11 +0000'
  date_gmt: '2010-01-17 20:07:11 +0000'
  content: Wow, That's pretty cool! I wan't aware of that!
- id: 230
  author: sl01k
  author_email: sl01k@o2.pl
  author_url: ''
  date: '2010-01-21 22:29:02 +0000'
  date_gmt: '2010-01-21 21:29:02 +0000'
  content: "hmm \r\nnice article but in my opinion this is bad way for styling...
    \r\nwhy ? \r\n\r\n- you create not semantic css\r\n- you have to much css ...\r\n-
    if you do on this way huge website you will be have huge mees in css. .. \r\n\r\nso
    i think that this is bad practice ... \r\n\r\nbut of course .. easy  to use and
    sometimes nice\r\ni prefer using the power of selectors \"&gt;\", \"+\" and semantic
    names for class ...  \r\n\r\none tip ... - may by you should try use a CSS freamwork
    ? \r\ni think in this time this is the best practice :) \r\n\r\nregards \r\nmarek
    m"
- id: 231
  author: Pawel
  author_email: pawel@pawelmartuszewski.co.uk
  author_url: http://www.pawelmartuszewski.co.uk
  date: '2010-01-21 22:53:58 +0000'
  date_gmt: '2010-01-21 21:53:58 +0000'
  content: "Marek,\r\n\r\nThanks for your feedback... and I see where are you coming
    from ;) But I think you missed the purpose of this demonstration...\r\n\r\nLet
    me clarify few things...\r\n\r\n- First of all. I didn't say anything about recommendations
    and this is a bad practice to use on a daily basis. The purpose was to demonstrate
    the possibilities and make people aware, because sometimes we don't have a choice
    and we have to style the element this way - forced by platform (eg. Wordpress
    navigation) etc.\r\n\r\n- \">\" and \"+\" selectors ? fine! ;) but they will not
    allow us to accomplish the task demonstrated in this tutorial (style element if
    CSS union) and what if it comes to IE6 and compatibility? ;)\r\n\r\n- CSS framework?
    Are you joking? CSS is too easy to use framework on ;)\r\n\r\nHope this clarifies
    a few things..."
- id: 233
  author: sl01k
  author_email: sl01k@o2.pl
  author_url: ''
  date: '2010-01-21 23:02:29 +0000'
  date_gmt: '2010-01-21 22:02:29 +0000'
  content: "i dont care (like youtube) about ie6 ... \r\nand OK :) i understand this
    is to demonstrate the possibilities, not recommendations"
- id: 364
  author: chucklesThePig
  author_email: chuckles@yahoo.com
  author_url: http://booger.com
  date: '2010-04-28 15:35:21 +0100'
  date_gmt: '2010-04-28 14:35:21 +0100'
  content: Man oh man - this is handy. Thanks! Multi-selector fun in Magento!
---
<img class="fl_lft thumb m_b_20" width="154" height="154" title="appling style to union class element" alt="applying style to union class element" src="http://www.pawelmartuszewski.co.uk/tuts/css_double_class/css_union.jpg"/>Using CSS, you can apply multiple styles to one HTML element. This is obvious and helps to keep our HTML and CSS clean and redundant. What happens if we want to style the element differently ONLY if two different classes applied?
<a href="http://www.pawelmartuszewski.co.uk/tuts/css_double_class/" target="_blank" title="multi class union demo" class="btn btn_demo">demo</a><a href="http://www.pawelmartuszewski.co.uk/tuts/css_double_class/css_m_classes.zip" class="btn btn_source"></a>

<div class="cl space">&nbsp;</div>
<h2>CSS standard multiple class styling</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

It is nothing special and new that we are allowed to apply multiple CSS styles to one HTML element. It helps to keep our CSS clear and clean and can reduce our CSS size drastically. This can be accomplished as shown below:
<div class="pre">
&lt;div class=&quot;style_1 style_2&quot;&gt; &lt;/div&gt;
</div>
Situation gets more complicated if we would like to style the element differently ONLY if two classes are applied. CSS multiple class styling with the different style on multi-class elements. 

<h2>Let's create 3 different classes and apply them to our div elements.</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<p class="p_b_0">CSS styles looks like this:</p>
<div class="pre">
div.border {
	border: 1px solid #333 ;
}
div.background {
	background-color: #9f9f9f ;	
}
div.shadow {
	text-shadow: #333 1px 1px;
}
</div>
<p class="p_b_0">Our HTML reads:<p>
<div class="pre">
&lt;div class=&quot;border&quot;&gt;.border&lt;/span&gt;&lt;/div&gt;<br />
&lt;div class=&quot;background&quot;&gt;.background&lt;/div&gt;<br />
&lt;div class=&quot;shadow&quot;&gt;.shadow&lt;/div&gt;
</div>
<p class="p_b_0">The effect is obvious:</p>
<img alt="applied one style to each div element" src="/tuts/css_double_class/1.jpg" title="applied one style to each div element">
<h2>Apply a different styles to elements that contain 2 or more CSS classes!</h2> 
<div class="dev"><div class="dev_in">&nbsp;</div></div>

Basicly if the element have <strong>.background</strong> and <strong>.border</strong> classes assigned to itself, we would like to change the color. And another element, if 3 classes are assigned we would like to add uppercase styling.

<p class="p_b_0">Add this to our existing CSS:</p>
<div class="pre">
/* ---- Now the fun begins! ---- */
div.border.background {
	color: #44c6ec;
}
div.border.background.shadow {
	text-transform:uppercase;
}
</div>
<p class="p_b_0">And add 2 more DIV tags:</p>
<div class="pre">
&lt;div class=&quot;border background&quot;&gt;.border.background&lt;/div&gt;<br />
&lt;div class=&quot;border background shadow&quot;&gt;.border.background.shadow&lt;/div&gt;
</div>
<p class="p_b_0">Our final result:</p>
<img alt="apply different style to element containing multiple classes" src="/tuts/css_double_class/3.png" title="apply different style to element containing multiple classes">

This is it! I hope you liked it. Don't forget to share and comment below!
