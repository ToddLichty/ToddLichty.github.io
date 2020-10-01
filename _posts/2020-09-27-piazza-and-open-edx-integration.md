---
layout: post
title: Piazza and Open edX Integration
permalink: /piazza-and-open-edx-integration/
author: Todd Lichty
---
I recently had to investigate the potential of integrating [Piazza](https://piazza.com/) with Open edX. We currently use Piazza as an online forum where students can ask (and answer) questions. The instructors also monitor Piazza to assist students with any issues they may be having.

I was lucky that Piazza offers LTI integration. Configuring the LTI integration with Open edX was very straightforward. Piazza offers detailed instructions here: https://piazza.com/product/lti

After configuring the integration and adding an LTI Xblock to a page, the “integration” was complete:

<img src="/images/piazza_integration.jpg" />

There is a “Launch Piazza” button to the right of the XBlock. Clicking the button will open a new tab with Piazza loaded to the linked class. 

If this is the first time that the user has tried launching Piazza from within Open edX, they will be asked to link their existing Piazza account or create a new one. In both instances, they are emailed a verification code that they need to enter to continue to the Piazza class. 

After the initial setup, the user can click the "Launch Piazza" button without having to login. 

Open edX passes the user’s role to piazza automatically. Instructors in Open edX are logged into piazza as instructors; students as students.

The integration was not a smooth as we would have liked. We decided to use the build in Open edX forums rather than using Piazza.
