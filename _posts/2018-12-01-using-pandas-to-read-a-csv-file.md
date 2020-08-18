---
layout: post
title: Using Pandas to Read a CSV File
permalink: /using-pandas-to-read-a-csv-file/
author: Todd Lichty
---
<p>In my quest to get up to speed on Python, I came across a problem where I needed to read a CSV file and import it into a database. Below are the steps I took to install p<a href="https://pandas.pydata.org/">andas</a> as well as a quick example of how to use the package.</p><p>First, I created a virtual environment to use for the project from a terminal window:</p><pre><code>python3 -m venv pandas
source pandas/bin/activate</code></pre><p>Next, I installed pandas using pip:</p><pre><code>pip install pandas</code></pre><p>Below is a sample python file that I created while playing with the pandas package. The code comments explain what the code does. </p><pre><code>import pandas as pd

# Read a csv file from the internet and print out the dataframe
url_csv = 'https://vincentarelbundock.github.io/Rdatasets/csv/boot/amis.csv'
df = pd.read_csv(url_csv, index_col=0)
print(df.head())

# Iterate over all the rows and print out the value in the 
for index, row in df.iterrows():
    print(index, row['speed'])

# Read a csv file from the internet and print out the first 7 rows from the dataframe
csv_url = 'http://vincentarelbundock.github.io/Rdatasets/csv/carData/MplsStops.csv'
df = pd.read_csv(csv_url, index_col='idNum')
print(df.iloc[:, 0:6].head())

# Read specific columns from the csv file and print out the first 7 rows from the dataframe
df = pd.read_csv(csv_url, index_col='idNum', usecols=['idNum', 'date', 'problem', 'MDC'])
print(df.iloc[:, 0:6].head())

# Get a tuple representing the dimensions of the frame (rows, columns)
print(df.shape)</code></pre><p>A very light weight and easy to use library. I was up and running in under 10 minutes.</p><p>I found two very useful articles on using pandas at the links below:</p><p><a href="https://www.marsja.se/pandas-read-csv-tutorial-to-csv/">Pandas Read CSV Tutorial</a></p><figure class="kg-card kg-embed-card"><iframe width="480" height="270" src="https://www.youtube.com/embed/videoseries?list=PLeo1K3hjS3uuASpe-1LjfG5f14Bnozjwy" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></figure>