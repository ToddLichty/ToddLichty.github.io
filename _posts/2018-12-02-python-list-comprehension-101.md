---
layout: post
title: Python List Comprehension 101
permalink: /python-list-comprehension-101/
author: Todd Lichty
---
<p>Below are some notes I took when first learning Python list comprehension. They have come in handy many times.</p><p>For each example, I show how it would be completed using a <em>for</em> loop and how it would be completed using list comprehension.</p><p><strong>Example 1: Copy items from one list to another</strong></p><pre><code>nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Make a new list with the same elements of nums
new_list = []

for i in nums:
    new_list.append(i)

print(new_list)

# Make a new list with the same elements of nums
new_list2 = [i for i in nums]
print(new_list2)</code></pre><p><strong>Example 2: Double to values in list one and add them to a new list</strong></p><pre><code>nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Make a new list with the each of the elements doubled
new_list = []

for i in nums:
    new_list.append(i * 2)

print(new_list)

# Make a new list with the each of the elements doubled
new_list2 = [i*2 for i in nums]
print(new_list2)</code></pre><p><strong>Example 3: Create a new list with the squares of the even items</strong></p><pre><code>nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Make a new list with the squares of the even numbers
new_list = []

for i in nums:
    if (i % 2 == 0):
        new_list.append(i*i)

print(new_list)

# Make a new list with the each of the elements doubled
new_list2 = [i*i for i in nums if i % 2 == 0]
print(new_list2)</code></pre><p><strong>Example 4: Create a (letter, number) pair for each letter in 'wxyz' and each number in '9876'</strong></p><pre><code># Create a (letter, number) pair for each letter in 'wxyz' and each number in '9876'
new_list = []
for letter in 'wxyz':
    for number in range(9, 5, -1):
        new_list.append((letter, number))

print(new_list)

new_list = [(letter, number) for letter in 'wxyz' for number in range(9, 5, -1)]
print(new_list)</code></pre>