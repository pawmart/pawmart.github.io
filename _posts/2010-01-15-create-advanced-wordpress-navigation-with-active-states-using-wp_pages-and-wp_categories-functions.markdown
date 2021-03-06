---
layout: post
status: publish
published: true
title: Create custom wordpress navigation with active state using wp_list_pages(); and wp_list_categories();
excerpt: 'Wordpress navigation can be tricky to create and sometimes we are not able
  to create it as we want. Problems starts if our website structure forces us to display
  categories, pages and home buttons and keep the active status even if deep into
  the category structure. This tutorial will explain how to accomplish just that. '
wordpress_id: 1281
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=1281
date: 2010-01-15 20:30:58.000000000 +00:00
tags:
- Wordpress
- Navigation
---

<p><img class="fl_lft thumb m_b_20" width="154" height="154" title="custom wordpress navigation" alt="custom wordpress navigation" src="http://www.pawelmartuszewski.co.uk/tuts/custom_wp_nav/custom_wp_nav.png"/>Wordpress navigation can be tricky to create and sometimes we are not able to create it as we want. Problems starts if our website structure forces us to display categories, pages and home buttons and keep the active status even if deep into the category strucutre. This tutorial will explain how to acomplish just that.</p>
<p class="b">Looking for demo? This website is the demo of this tutorial.</p>

<h2>What we are going to create</h2>
<p>We are going to create a custom wordpress navigation similar to this one on this website. One navigation containing home page button, page buttons and category buttons and active state.</p>

<h2>Our navigation structure</h2>
<p>We would like to display the home button followed by pages, followed by our main categories. The navigation structure code is:</p>
{% highlight html %}
<ul id="nav">
<li <?php if (is_home()){echo 'class="current_page_item"';}?>><a href="<?php bloginfo('url'); ?>">Home<a><li>
<?php wp_list_pages('title_li=&amp;include=10,11,12'); ?>
<?php wp_list_categories('orderby=order&amp;title_li=&amp;depth=1&amp;hide_empty=0'); ?>
</ul>;
{% endhighlight %}
<p>As you can see, first LI tag is to display our home button and if we are on home page, manually assign the class called <strong>current_page_item</strong>. Next we want to display 3 pages (in this case the pages with id 10,11,12) and next we would like to display our main categories and we do so by setting depth to 1 (display only main categories).</p>

<h2>Wordpress Home Button -  if (is_home())</h2>
<p>Nothing complicated here. This button will link to our home page and will have the CSS class <strong>current_page_item</strong> as explained above. To make the <strong>active state</strong> we just need to define the style in our CSS, that we want for this class.</p>

<h2>Wordpress Pages -  wp_list_pages();</h2>
<p>We display here our pages and to make the active state for those buttons will be defined again under the class <strong>current_page_item</strong> (class generated by wp_list_pages(); function and assigned to LI tags), the same as for our home page button.</p>
<p class="b">Note: To make sure our button is active even if we are on the child page and childs of the child, need to style the same "current_page_parent" and "current_page_ancestor". </p>

<h2>So our stylesheet reads as follows:</h2>
{% highlight css %}
#nav.current_page_item a,
#nav.current_page_parent a,
#nav.current_page_ancestor a {
    /* our styles for active state goes here */
}
{% endhighlight %}

<h2>Wordpress Categories -  wp_list_categories();</h2>
<p>Situation gets more tricky if it comes to categories. We have got our main categories displayed and it seems easy to <strong>create the active state</strong>. The style we would need to define is <strong>current-cat</strong> (generated by wp_list_categories), but we are not going to do it. Why? This will allow us to create the <strong>active state</strong> only if we are on the main <strong>category page</strong>, but we want to keep the active state even if on child category and even if on child category post. </p>
<p>To do so, we need to download the plugin called <a href="http://www.screenshine.net/blog/1474_wordpress-plugin-show-active-category" title="Show Active Category - Plugin" target="_blank">Show Active Category</a> from <a href="http://www.screenshine.net/blog/1474_wordpress-plugin-show-active-category" title="Screenshine - Blog" target="_blank">Screenshine</a>.</p>

<p>Upload it to your plugins folder and activate it in your wordpress control panel.</p>

<h2>Now go and edit this plugin and locate the following line:</h2>
{% highlight php %}
if ( is_single() ) {
{% endhighlight %}

<h2>and replace it to look like this:</h2>
{% highlight php %}
if ( is_single() || is_category() ) {
{% endhighlight %}
<p>This will allow us to display the active class on our button if we browse post or category. Now our buttons will have "active_category" class assigned to anchor element.</p>
<p class="b">Note one important thing. The class is assigned to the "a" element not "li" tag (like it was for pages), so adjust you CSS to fit just that.</p>

<h2>Our CSS looks now:</h2>
{% highlight css %}
#nav li.current_page_item a,
#nav li.current_page_parent a,
#nav li.current_page_ancestor a,
#nav li a.active_category {
    /* our styles for active state goes here */
}
{% endhighlight %}

<h2>More about Active State Buttons</h2>
<p>If this still if not enough to control your categories, you can use <a href="http://wordpress.org/extend/plugins/my-category-order/" title="My Category Order - Plugin" target="_blank">display category order</a> plugin to take control over the <strong>category order</strong>.</p>
<p>If this is not enough and your <strong>navigation requires advanced styling</strong>, you will be forced to use some CSS tricks. As we are unable to assign any CSS id to the list items we will have to use <strong>multi-class union CSS trick</strong>. More info can be found on this tutorial: <a href="http://www.pawelmartuszewski.co.uk/web_tutorials/appling-style-to-element-if-multi-class-union/" title="Read this Entry">Applying style to an element only if multi-class union exist</a>.</p>

<h2>Conclusion</h2>
<p>As you can see, we have a control over the <strong>wordpress navigation</strong> and things aren't that complicated if we know what we are doing. If you use different techiniques or recommend to do it a little bit different (improve it), feel free to leave a comment. I hope you like it.</p>
<p>Agh, and don't forget to share this tutorial with others. ;)</p>
