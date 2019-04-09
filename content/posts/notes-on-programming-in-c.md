---
title: "Notes on Programming in C"
date: 2018-03-31T22:23:43-04:00
draft: false
---
Good read: <a href="http://doc.cat-v.org/bell_labs/pikestyle">Notes on programming in C</a> by Rob Pike.

On complexity:
```
Rule 1.  You can't tell where a program is going to spend its time.  
         Bottlenecks occur in surprising places, so don't try 
         to second guess and put in a speed hack until you've 
         proven that's where the bottleneck is.

Rule 2.  Measure.  
         Don't tune for speed until you've measured, and even then 
         don't unless one part of the code overwhelms the rest.

Rule 3.  Fancy algorithms are slow when n is small, and n is 
         usually small.  
         Fancy algorithms have big constants. 
         Until you know that n is frequently going to be big, 
         don't get fancy.

Rule 4.  Fancy algorithms are buggier than simple ones, and they're 
         much harder to implement.  Use simple algorithms as well as 
         simple data structures.

Rule 5.  Data dominates.  
         If you've chosen the right data structures and organized 
         things well, the algorithms will almost always be self-evident.  
         Data structures, not algorithms, are central to programming.


```