---
layout: post
title: Open edX SAML Integration with ADFS - Part 1
permalink: /open-edx-saml-integration-with-onelogin/
author: Todd Lichty
---
<p>I've spent the last week trying to integrate our Open edX instance with the university's ADFS provider. The initial setup was quick and easy. During the first login attempt, I had hopes that this would be a swift process, only to be presented by an error message:</p><figure class="kg-card kg-image-card"><img src="/images/login_error.png" class="kg-image"></figure><p>Initially, this seemed like a pretty straightforward error. Three days later, I was no further to solving this problem. I first took the reply from the server and validated that it was correctly signed by using the tools over at <a href="https://www.samltool.com/validate_response.php">SamlTools</a>. Everything seemed to work fine.</p><figure class="kg-card kg-image-card"><img src="/images/saml_tools.png" class="kg-image"></figure><p>After posting to the Open edX <a href="https://discuss.openedx.org/t/authentication-failed-saml-login-failed-invalid-response-signature-validation-failed-saml-response-rejected/790">Discourse</a> forum and not receiving any assistance, I made a list of possible causes on the whiteboard in my office:</p><!--kg-card-begin: markdown--><ol>
<li>Debug flag was set to allow logging of the SAML request and response. Maybe this was causing an issue?</li>
<li>Perhaps there was a time difference between the Open edX docker image and the ADFS server.</li>
<li>Open edX was not using the proper public key from the server.</li>
<li>Caching issue of some kind?</li>
<li>Wrong cipher was being used?</li>
</ol>
<!--kg-card-end: markdown--><p>After crossing 1, 2, 4 and 5 off my list, I was left with testing #3. All the settings and config values pointed to the fact that the public key reported by the server and the public key used by Open edX to validate the response were identical.</p><p>In the next post, I want to document my process for integrating Open edX with OneLogin SAML Test Connector.</p>