---
layout: post
title: Running a Subprocess from Python and Capturing the Output and Errors
permalink: /running-a-subprocess-from-python-and-capturing-the-output-and-errors/
author: Todd Lichty
---
<p>This post is more of a "scratchpad" post than anything else. I wanted to try a different method of running racket code that did not include docker. After some experimenting, I came up with the following Python code:</p><!--kg-card-begin: markdown--><pre><code>import subprocess

output = subprocess.run([&quot;racket&quot;, &quot;a6q1_solution.rkt&quot;], stdout=subprocess.PIPE, stderr=subprocess.PIPE)

print(output.stdout)
print(output.stderr)
</code></pre>
<!--kg-card-end: markdown--><p>Everything in Python is quick and easy. It is unclear which method I will be utilizing to run the code but this certainly looks clean and simple.</p>