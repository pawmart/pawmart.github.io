---
layout: post
status: publish
published: true
title: Generate random string of characters in PHP
author: Pawel
author_login: admin
author_email: pawel@pawelmartuszewski.co.uk
author_url: http://www.pawelmartuszewski.co.uk
excerpt: In this very short tutorial, I am going to show you how to ceate a flexible
  php function. This function will allow you to generate random string of your choosen
  characters and your choosen length. Let's create the php function!
wordpress_id: 1429
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=1429
date: 2010-02-13 22:54:04.000000000 +00:00
categories:
- Tutorials
- PHP / MySQL
tags:
- PHP
comments:
- id: 325
  author: Dan
  author_email: daniel4443@gmail.com
  author_url: ''
  date: '2010-03-14 00:53:42 +0000'
  date_gmt: '2010-03-13 23:53:42 +0000'
  content: Exactly what I was looking for! Thanks man!
- id: 522
  author: Teiya
  author_email: rss@fd.mk.ua
  author_url: http://www.google.com/
  date: '2011-05-07 17:46:49 +0100'
  date_gmt: '2011-05-07 16:46:49 +0100'
  content: Thanks for sharing. Awayls good to find a real expert.
---
<img class="fl_lft thumb m_b_20" width="154" height="154" alt="Generate random string of characters in PHP" src="http://www.pawelmartuszewski.co.uk/tuts/generate_random_string/img.jpg" />In this very short tutorial, I am going to show you how to ceate a flexible php function. This function will allow you to generate random string of your choosen characters and your choosen length. Let's create the php function!
<a class="btn btn_demo" href="http://www.pawelmartuszewski.co.uk/tuts/generate_random_string/demo.php" title="Generate random string of characters - Demo">Demo</a>
<div class="cl">&nbsp;</div>

<h2>Starting our function</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<div class="pre">
<?php<br />
function random_string($chars, $length) {
</div>
<h2>Assigning strings to variables</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<div class="pre">
<span class="b">// Assign strings to variables</span>
$lc = 'abcdefghijklmnopqrstuvwxyz'; <span class="b">// lowercase</span>
$uc = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'; <span class="b">// uppercase</span>
$nr = '1234567890'; <span class="b">// numbers</span>
$sp = '^@*+-+%()!?'; <span class="b">//special characters</span>
</div>
<h2>Creating switch for different chars selection</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<div class="pre">
<span class="b">// Set cases for our characters</span>
switch ($chars) {<br />
case 'lower': $chars = $lc; break;<br />
case 'upper': $chars = $uc; break;<br />
case 'numbers': $chars = $nr; break;<br />
case 'special': $chars = $sp; break;<br />
case 'all': $chars = $lc.$up.$nr.$sp; break;<br />
}
</div>
You can specify more cases to suit your needs if it comes to character selection.
<h2>Processing (core of our function)</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<div class="pre">
<span class="b">// Length of character list</span>
$chars_length = (strlen($chars) - 1);<br />
<span class="b">// Start our string</span>
$string = $chars{rand(0, $chars_length)};<br />
<span class="b">// Generate random string</span>
for ($i = 1; $i &lt; $length; $i = strlen($string))<br />
{<br />
<span class="b">// Take random character from our list</span>
$random = $chars{rand(0, $chars_length)};<br />
<span class="b">// Make sure the same two characters don't appear next to each other</span>
if ($random != $string{$i - 1}) $string .=  $random;<br />
}
</div>
<h2>Return variable</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<div class="pre">
<span class="b">//return our generated string</span>
return $string;<br />
}
</div>
<h2>Echoing our function with different parameters</h2>
<div class="dev"><div class="dev_in">&nbsp;</div></div>
<div class="pre">
<?php<br />
echo random_string('lower',20); <span class="b">// generates lowercase string - 20 chars length</span>
echo random_string('upper',20); <span class="b">// generates uppercase string - 20 chars length</span>
echo random_string('numbers',10); <span class="b">// generates numbers string - 10 chars length</span>
echo random_string('special',40); <span class="b">// generates special chars string - 40 chars length</span>
echo random_string('all',50); <span class="b">// generates all chars string - 50 chars length</span>
</div>

Well, you've got the idea.

Feel free to share yours techniques to generate random string in php. Don't forget to share it with others and subscribe to my newsletter!
