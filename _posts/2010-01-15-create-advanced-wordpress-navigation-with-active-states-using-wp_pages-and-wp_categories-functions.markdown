---
layout: post
status: publish
published: true
title: Create custom wordpress navigation with active state using wp_list_pages();
  and wp_list_categories();
author: Pawel
author_login: admin
author_email: pawel@pawelmartuszewski.co.uk
author_url: http://www.pawelmartuszewski.co.uk
excerpt: 'Wordpress navigation can be tricky to create and sometimes we are not able
  to create it as we want. Problems starts if our website structure forces us to display
  categories, pages and home buttons and keep the active status even if deep into
  the category strucutre. This tutorial will explain how to acomplish just that. '
wordpress_id: 1281
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=1281
date: 2010-01-15 20:30:58.000000000 +00:00
categories:
- Tutorials
- CSS Tutorials
- Wordpress Tutorials
tags:
- Wordpress
- Navigation
comments:
- id: 208
  author: Dan
  author_email: dan@wp.pl
  author_url: ''
  date: '2010-01-17 21:09:09 +0000'
  date_gmt: '2010-01-17 20:09:09 +0000'
  content: "Your explanation is very clean. Now I am not afraid of wordpress navigation
    strucutre!\r\n\r\nVery well done Pawel. Thanks. \r\n\r\nWill visit again."
- id: 209
  author: Pawel
  author_email: pawel@pawelmartuszewski.co.uk
  author_url: http://www.pawelmartuszewski.co.uk
  date: '2010-01-17 21:10:27 +0000'
  date_gmt: '2010-01-17 20:10:27 +0000'
  content: I am glad you like it! ;)
- id: 265
  author: ray ban store
  author_email: joansmith0999@gmail.com
  author_url: http://www.raybanstore.co.uk
  date: '2010-02-04 01:19:41 +0000'
  date_gmt: '2010-02-04 00:19:41 +0000'
  content: "I enjoyed the article and thanks recompense posting such valuable tidings
    emoluments of all of us to own,  I start it both of around and revelatory and
    I blueprint to arrange it as one of these days as I can.\r\n\r\n<a href=\"http://www.raybanstore.co.uk\"
    rel=\"nofollow\">ray ban 3025</a>"
- id: 365
  author: piyashrija
  author_email: wp_design_shrijan@hotmail.com
  author_url: http://www.agriculturecommercialization.com
  date: '2010-05-07 14:21:18 +0100'
  date_gmt: '2010-05-07 13:21:18 +0100'
  content: thank very much after 2 days of search i tried this post and it work for
    me :))))
- id: 388
  author: Dave
  author_email: drdavesgraphics@gmail.com
  author_url: http://davedavisphotography.com
  date: '2010-06-13 21:40:10 +0100'
  date_gmt: '2010-06-13 20:40:10 +0100'
  content: "Oh man, You ROCK!! Your a GOD... Thanks so much for posting the Active
    Home scriptlet!!\r\n\r\nAll the best\r\nDave"
- id: 389
  author: Gucci Shoes
  author_email: joansmith0999@gmail.com
  author_url: http://www.guccidiscountstore.com
  date: '2010-06-17 08:32:55 +0100'
  date_gmt: '2010-06-17 07:32:55 +0100'
  content: "Cheers for posting this.  Thanks\r\n<a href=\"http://www.guccidiscountstore.com\"
    rel=\"nofollow\">Discount Gucci Shoes</a>"
- id: 455
  author: darian
  author_email: creadavide@yahoo.it
  author_url: http://workingonit!
  date: '2010-09-01 17:38:13 +0100'
  date_gmt: '2010-09-01 16:38:13 +0100'
  content: Thanks for sharing that! it 's been ages I was looking for it!
- id: 494
  author: Hillary Guerra
  author_email: hillaryguerra@gmail.com
  author_url: http://hillaryguerra.co.cc/
  date: '2010-12-23 22:47:19 +0000'
  date_gmt: '2010-12-23 21:47:19 +0000'
  content: Oh man, You ROCK!! Your a GOD... Thanks so much for posting the Active
    Home scriptlet!! All the best Dave
- id: 537
  author: 'WordPress custom theme tutorial: how to create a Navigation Menu | tutorials
    blogs'
  author_email: ''
  author_url: http://tutorialsblogs.com/wordpress-custom-theme-tutorial/
  date: '2011-11-13 11:40:32 +0000'
  date_gmt: '2011-11-13 10:40:32 +0000'
  content: '[...] This is a list of great tutorials on how to build your own custom
    menu for your WordPress Theme: Create custom wordpress navigation with active
    state using wp_list_pages(); and wp_list_categories()... [...]'
---
<img class="fl_lft thumb m_b_20" width="154" height="154" title="custom wordpress navigation" alt="custom wordpress navigation" src="http://www.pawelmartuszewski.co.uk/tuts/custom_wp_nav/custom_wp_nav.png"/>Wordpress navigation can be tricky to create and sometimes we are not able to create it as we want. Problems starts if our website structure forces us to display categories, pages and home buttons and keep the active status even if deep into the category strucutre. This tutorial will explain how to acomplish just that. 

<p class="b">Looking for demo? This webiste is the demo of this tutorial.</p>
<div class="cl space">&nbsp;</div>
<h2>What we are going to create</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

We are going to create a custom wordpress navigation similar to this one on this website. One navigation containing home page button, page buttons and categoriy buttons and active state.

<img src="/tuts/custom_wp_nav/1.png" alt="custom wordrpess navigation"/>

<h2>Our navigation structure</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

We would like to display the home button followed by pages, followed by our main categories. The navigation structure code is:
<div class="pre">
&lt;ul id=&quot;nav&quot;&gt;<br />
&lt;li &lt;?php if (is_home()){echo 'class=&quot;current_page_item&quot;';}?&gt;&gt;&lt;a href=&quot;&lt;?php bloginfo('url'); ?&gt;/&quot;&gt;Home&lt;/a&gt;&lt;/li&gt;<br />
&lt;?php wp_list_pages('title_li=&amp;include=10,11,12'); ?&gt;<br />
&lt;?php wp_list_categories('orderby=order&amp;title_li=&amp;depth=1&amp;hide_empty=0'); ?&gt;<br />
&lt;ul&gt;
</div>
As you can see, first LI tag is to display our home button and if we are on home page, manually assign the class called <strong>current_page_item</strong>. Next we want to display 3 pages (in this case the pages with id 10,11,12) and next we would like to display our main categories and we do so by setting depth to 1 (display only main categories).

<h2>Wordpress Home Button -  if (is_home())</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

Nothing complicated here. This button will link to our home page and will have the CSS class <strong>current_page_item</strong> as explained above. To make the <strong>active state</strong> we just need to define the style in our CSS, that we want for this class.

<h2>Wordpress Pages -  wp_list_pages();</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

We display here our pages and to make the active state for those buttons will be defined again under the class <strong>current_page_item</strong> (class generated by wp_list_pages(); function and assigned to LI tags), the same as for our home page button. 

<p class="b">Note: To make sure our button is active even if we are on the child page and childs of the child, need to style the same "current_page_parent" and "current_page_ancestor". </p>

<h2>So our stylesheet reads as follows:</h2>
<div class="pre">
#nav.current_page_item a,
#nav.current_page_parent a,
#nav.current_page_ancestor a {
     /* our styles for active state goes here */
}
</div>

<h2>Wordpress Categories -  wp_list_categories();</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

Situation gets more tricky if it comes to categories. We have got our main categories displayed and it seems easy to <strong>create the active state</strong>. The style we would need to define is <strong>current-cat</strong> (generated by wp_list_categories), but we are not going to do it. Why? This will allow us to create the <strong>active state</strong> only if we are on the main <strong>category page</strong>, but we want to keep the active state even if on child category and even if on child category post. 

To do so, we need to download the plugin called <a href="http://www.screenshine.net/blog/1474_wordpress-plugin-show-active-category" title="Show Active Category - Plugin" target="_blank">Show Active Category</a> from <a href="http://www.screenshine.net/blog/1474_wordpress-plugin-show-active-category" title="Screenshine - Blog" target="_blank">Screenshine</a>. 

Upload it to your plugins folder and activate it in your wordpress control panel.

<h2>Now go and edit this plugin and locate the following line:</h2>
<div class="pre">
if( is_single()) {
</div>
<h2>and replace it to look like this:</h2>
<div class="pre">
if( is_single() || is_category() ) {
</div>
This will allow us to display the active class on our button if we browse post or category. Now our buttons will have "active_category" class assigned to anchor element.

<p class="b">Note one important thing. The class is assigned to the "a" element not "li" tag (like it was for pages), so adjust you CSS to fit just that.</p>

<h2>Our CSS looks now:</h2>
<div class="pre">
#nav li.current_page_item a,
#nav li.current_page_parent a,
#nav li.current_page_ancestor a,
#nav li a.active_category {
     /* our styles for active state goes here */
}
</div>

<h2>More about Active State Buttons</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>

If this still if not enough to control your categories, you can use <a href="http://wordpress.org/extend/plugins/my-category-order/" title="My Category Order - Plugin" target="_blank">display category order</a> plugin to take control over the <strong>category order</strong>.

If this is not enough and your <strong>navigation requires advanced styling</strong>, you will be forced to use some CSS tricks. As we are unable to assign any CSS id to the list items we will have to use <strong>multi-class union CSS trick</strong>. More info can be found on this tutorial: <a href="http://www.pawelmartuszewski.co.uk/web_tutorials/appling-style-to-element-if-multi-class-union/" title="Read this Entry">Applying style to an element only if multi-class union exist</a>.

<h2>Conclusion</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
As you can see, we have a control over the <strong>wordpress navigation</strong> and things aren't that complicated if we know what we are doing. If you use different techiniques or recommend to do it a little bit different (improve it), feel free to leave a comment. I hope you like it.

Agh, and don't forget to share this tutorial with others. ;)
