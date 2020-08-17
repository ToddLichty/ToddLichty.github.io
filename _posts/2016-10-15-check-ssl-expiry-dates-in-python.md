---
layout: post
title: Check SSL Expiry Dates in Python
permalink: /check-ssl-expiry-dates-in-python/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>It seems pretty self explanatory why SSL certificates need to expire. Everyone knows that they expire. Why is it SOOOO hard to remember to renew your certificate? We've been bit twice in the past three months with certificates that have expired on us. We do the mad scramble to get the renewed and then forget about them again.</p>
<p>Rather than continue down this never ending path, I decided to write a quick script that could be run nightly on our Raspberry Pi to use a JSON feed of all the SSL sites that we have, check the SSL certificate expiry date and then notify me if one of the sites is expiring in the next 30 days.</p>
<p>Below is a redacted version of the code. It needs some error handling added for sure.</p>
<pre><code>#!/usr/bin/python
import datetime
import socket
import ssl
from urlparse import urlparse
import urllib2, json
import email.message
import smtplib

def sendEmail( subject, body ):
	try:
		msg = email.message.Message()
		msg['Subject'] = subject + &quot; - SSL monitoring&quot;
		msg['From'] = 'sslmonitor@sherpamarketing.ca'
		msg['To'] = 'tlichty@sherpamarketing.ca'
		msg.add_header('Content-Type','text/html')
		msg.set_payload(body)

		s = smtplib.SMTP('retail.smtp.com', 2525)
		s.login('USERNAME', 'PASSWORD')
		s.sendmail(msg['From'], [msg['To']], msg.as_string())
	except:
		print(&quot;smtp error&quot;)

	return;

#This was modified from https://serverlesscode.com/post/ssl-expiration-alerts-with-lambda/
def ssl_expiry_datetime(hostname):
    ssl_date_fmt = r'%b %d %H:%M:%S %Y %Z'

    context = ssl.create_default_context()
    conn = context.wrap_socket(
        socket.socket(socket.AF_INET),
        server_hostname=hostname,
    )
    # 3 second timeout because Lambda has runtime limitations
    conn.settimeout(3.0)

    conn.connect((hostname, 443))
    ssl_info = conn.getpeercert()
    # parse the string from the certificate into a Python datetime object
    return datetime.datetime.strptime(ssl_info['notAfter'], ssl_date_fmt)

url = &quot;http://URL_OF_JSON_FEED&quot;
response = urllib2.urlopen(url)
data = json.loads(response.read())

now = datetime.datetime.now()
for di in data:
	o = urlparse(di)
	expirationDate = ssl_expiry_datetime(o.netloc)
	delta = expirationDate - now
	if delta.days &lt; 30:
		sendEmail(di, &quot;SSL cert expires in &quot; + str(delta.days) + &quot; days&quot;)
</code></pre>
<p>I added this script as a cron job to our Raspberry Pi and it has been running successfully ever since. I should also add in slack notifications. Something for the future. :)</p>
<!--kg-card-end: markdown-->