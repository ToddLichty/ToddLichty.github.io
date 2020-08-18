---
layout: post
title: Running Python in the Web Browser
permalink: /running-python-in-the-web-browser/
author: Todd Lichty
---
<p>A significant part of the project I am currently working on involves executing code submitted by the user. Every bone in my body screams at the fact that the project will accept code from the user and then execute it. A good chunk of the past 20 years I’ve spent as a web developer has revolved around hardening web projects so that user input is NEVER executable.</p><p>To solve this problem, I have investigated many different options. One of the great things about working at a university is that research and development are given very high priority. This has given me ample opportunities to learn and experiment with a wide variety of technologies. One technology that I came across was a project by <a href="https://www.mozilla.org/en-CA/">Mozilla</a> called <a href="https://github.com/iodide-project/pyodide">Pyodide</a>. </p><p><strong>What is Pyodide?</strong></p><p>From this <a href="https://hacks.mozilla.org/2019/04/pyodide-bringing-the-scientific-python-stack-to-the-browser/">article</a>: </p><blockquote>“Pyodide is an experimental project from Mozilla to create a full Python data science stack that runs entirely in the browser.”</blockquote><p>Let that sink in. <a href="https://github.com/iodide-project/pyodide">Pyodide</a> allows Python code (and a number of the most powerful modules) to run entirely in the browser. No downloading and installing software. No worrying about multiple versions on the user’s machine. No executing user code on the server!</p><p>Mozilla was able to make this magic happen by utilizing <a href="https://webassembly.org/">WebAssembly</a>. WebAssembly allows C and Rust code to be compiled and run within a web browser. The wizards over at Mozilla were able to use the cpython-emscripten project to convert the Python interpreter into WebAssembly. Python becomes a first class citizen in the browser similar to JavaScript.</p><p><strong>Sample Code</strong></p><p>This project can be found at <a href="https://github.com/ToddLichty/pyodide_test">https://github.com/ToddLichty/pyodide_test</a></p><figure class="kg-card kg-image-card"><img src="/images/pyodide_sample.png" class="kg-image"></figure><p>I used the <a href="https://ace.c9.io/">Ace Code Editor</a> component in this sample since it is quick to embed and makes writing Python in a web browser feel more like writing in an IDE.</p><p>After writing code in the editor, clicking the Run Code!!! Button will execute the code in the Pyodide WASM compiler. The print statements are sent to the browser console by default, so I have to tie into the console log event to cause the output to show in the textarea above.</p><p>If we look at the project, you can see that Pyodide requires a few different files to work:</p><figure class="kg-card kg-image-card"><img src="/images/pyodide_project_files-1.png" class="kg-image"></figure><p>These files can be downloaded from the Pyodide website or built on your computer from the GitHub repository. </p><p>These files are not small. The WASM file itself is 9.5MB. However, with some clever caching, the user would only need to download the file once.</p><p>During the investigation of Pyodide, I was able to put it through it’s paces. I had to try and anticipate any coding issues that a user could make. Besides the standard syntax errors, I tested infinite loops, deep recursion, infinite recursion, mutual recursion etc. Stressing the WASM interpreter like this did cause the browser to crash pretty consistently. Is this an issue with Pyodide. No. The standard Python interpreter behaved the same way when running the same tests. </p><p>One issue that became apparent was that running code in Pyodide was approximately 10x slower than running it natively. Below are the results of some of the tests that were run.</p><!--kg-card-begin: markdown--><table>
<thead>
<tr>
<th>Algorithm</th>
<th style="text-align:right">Native</th>
<th style="text-align:right">Pyodide</th>
</tr>
</thead>
<tbody>
<tr>
<td>Recursive Fibonaci (35th element)</td>
<td style="text-align:right">2626</td>
<td style="text-align:right">26273</td>
</tr>
<tr>
<td>Prime factors of 67867979</td>
<td style="text-align:right">3437</td>
<td style="text-align:right">46551</td>
</tr>
<tr>
<td>Mutual Recursion</td>
<td style="text-align:right">8669</td>
<td style="text-align:right">83319</td>
</tr>
</tbody>
</table>
<!--kg-card-end: markdown--><p>Pyodide is a really cool project. Hopefully, this is the start of possibly moving away from JavaScript and towards potentially using Python for client side scripting instead.</p>