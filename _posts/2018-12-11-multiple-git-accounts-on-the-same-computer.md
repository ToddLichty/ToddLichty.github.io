---
layout: post
title: Multiple Git Accounts on the Same Computer
permalink: /multiple-git-accounts-on-the-same-computer/
author: Todd Lichty
---
<p>I recently ran into a situation where I needed to be able to access both github and gitlabs on my laptop with different accounts. I had no clue where to begin but I found this article <a href="https://code.tutsplus.com/tutorials/quick-tip-how-to-work-with-github-and-multiple-accounts--net-22574">https://code.tutsplus.com/tutorials/quick-tip-how-to-work-with-github-and-multiple-accounts--net-22574</a>  which walked me through the setup process. My config file was slightly different than what was specified in the article:</p><pre><code>#Default GitHub
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa

#Gitlabs for Work
Host git.WORK_TLD.ca
  HostName git.uwaterloo.ca
  User git
  IdentityFile ~/.ssh/id_rsa_WORK</code></pre><p>Everything was pretty straightforward after that.</p>