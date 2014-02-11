---
layout: post
status: publish
published: true
title: Paypal IPN returns valid response in sandbox but invalid in production
author: Pawel
author_login: admin
author_email: pawel@pawelmartuszewski.co.uk
author_url: http://www.pawelmartuszewski.co.uk
wordpress_id: 2055
wordpress_url: http://www.pawelmartuszewski.co.uk/?p=2055
date: 2012-02-12 18:31:11.000000000 +00:00
categories:
- Code
- Articles
- Tutorials
- PHP / MySQL
tags:
- PHP
- Paypal
comments: []
---
<img  class="fl_lft thumb m_b_20" style="border:none !important;"  src="http://www.pawelmartuszewski.co.uk/wp-content/uploads/paypal.png" alt="paypal" title="paypal" width="154" height="154"/>I stumbled upon a very annoying paypal problem recently and I think this is a differently a good case to mention to others to save much trouble and time. The problem I had is Paypal IPN returning 'invalid' response in production (live environment) but all working correctly (including Paypal IPN test) in Paypal Sandbox.

<div class="cl"></div>
<h2>This is my final IPN listener:</h2>
<div class="dev"><div class="dev_in"></div></div>

<pre>
function validateIpn()
{

	$ipn_post_data = $_POST;

	 // Choose url
	if(array_key_exists('test_ipn', $ipn_post_data) &&
	 	1 === (int) $ipn_post_data['test_ipn']) {
	 $url = 'www.sandbox.paypal.com';
	} else {
	     $url = 'www.paypal.com';
	}

	$post_string = 'cmd=_notify-validate';
	foreach ($ipn_post_data as $key => $value)
	{
	$this->ipnData["$key"] = $value;

	$value = urlencode(stripslashes($value));
	$value = preg_replace('/(.*[^%^0^D])(%0A)(.*)/i','${1}%0D%0A${3}',$value);
	$post_string .= "&$key=$value";
	}

	$fp = fsockopen ($url, 80, $errno, $errstr, 30);
	$header = 'POST /cgi-bin/webscr HTTP/1.0' . "\r\n" .
	'Host: ' . $url . "\r\n" .
	'Content-Type: application/x-www-form-urlencoded' . "\r\n" .
	'Content-Length: ' . strlen($post_string) . "\r\n" .
	'Connection: close' . "\r\n\r\n";

	@fputs($fp, $header . $post_string);

	while (!@feof($fp))
	{
		$res = @fgets($fp, 1024);

			if (strcmp ($res, "VERIFIED") == 0) {

				// Valid IPN transaction.
				return true;

			} elseif (strcmp ($res, "INVALID") == 0) {

				// Invalid IPN transaction.  Check the log for details.
				$this->last_error = 'IPN Validation Failed.';
				return false;
			}

	}
	@fclose($fp);

}
</pre>


<h2>Hmm.. still no luck!</h2>
<div class="dev"><div class="dev_in"></div></div>

As it turns out nothing is wrong with the above listener and that took me a couple of days to figure that out including disputing with paypal on the phone. The issue is of course with encoing and if you checked everything else this is the biggest candidate you should vote on.

There are a couple of things to check:

<p class="b">
- are you sending a correct charset information in your POST to paypal? (make sure its utf-8)
- is charset set properly under you paypal settings? (again make sure its utf-8)
- turn on IPN response within paypal settings even if you have a custom url and you set it using your POST that you send to paypal
</p>

<h2>My $_POST method is setting charset here:</h2>
<pre>
// my method is using addField to pass it over
$this->addField('charset', 'utf-8');
</pre>

This is often a problem if a buyer name is foreign or your product name has any foreign character.

<h2>Paypal settings:</h2>
<div class="dev"><div class="dev_in"></div></div>

This can be found under Profile > Selling options...

<div class="hot">
<img src="http://www.pawelmartuszewski.co.uk/wp-content/uploads/paypalutf8.png" alt="paypalutf8" title="paypalutf8" width="622" height="294" class="alignnone size-full wp-image-2061" />
</div>

<div class="dev"><div class="dev_in"></div></div>

Hope this saves you some time as I struggled with it a lot.
