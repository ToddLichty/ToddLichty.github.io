---
layout: post
title: Issues Migrating To SQL Azure with Full Text Index
permalink: /issues-migrating-to-sql-azure-with-full-text-index/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I've been in the process of migrating our website from our current hosting provider over to Microsoft Azure. One of the issues that I ran into when migrating some of our older sites has to do with Full Text Indexes. When trying to use the SSMS migration tool, I received an error message stating that Full Text Indexes are not supported.</p>
<p>Some Googling quickly found this link:</p>
<p><a href="https://azure.microsoft.com/en-us/blog/full-text-search-is-now-available-for-preview-in-azure-sql-database/">https://azure.microsoft.com/en-us/blog/full-text-search-is-now-available-for-preview-in-azure-sql-database/</a></p>
<p>To perform the migration, I first deleted the indexes on the current database:</p>
<pre><code>DROP FULLTEXT INDEX ON table_name
</code></pre>
<p>I then ran the migration tool to migrate the database over to SQL Azure. After configuring the users and permissions, I then recreated the catalog and index:</p>
<pre><code>CREATE FULLTEXT CATALOG Search AS DEFAULT;

CREATE FULLTEXT INDEX ON dbo.table_name(column1,column2) KEY INDEX primary_key ON Search; 

ALTER FULLTEXT INDEX ON dbo.table_name ENABLE;

ALTER FULLTEXT INDEX ON dbo.table_name START FULL POPULATION;
</code></pre>
<!--kg-card-end: markdown-->