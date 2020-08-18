---
layout: post
title: Open edX - xblock - Author View
permalink: /open-edx-xblock-author-view/
author: Todd Lichty
---
<p>Quick tip: If you want to show an author_view for your custom xblock in the Open edX studio, you need to add a field to your Python file called has_author_view.</p><pre><code>class CodeEditorXBlock(XBlock):
	has_author_view = True</code></pre><p>This will cause the author_view method to be fired when showing the xblock in the studio.</p>