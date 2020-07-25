---
layout: page
title:  "Python - Key learnings"
subtitle: "Common pitfalls and difficulties as beginners - demystified"
date:   2020-07-01 21:21:21 +0530
categories: ["Python"]
---

## 1. Do not equate lists unless you are comfortable with pointers.
Not knowing this first one has personally cost me a tiny bit of my sanity while working on an assignment.  
Let us see a sample program to understand the problem.   
```
List_A = [1,2,3,'f','g','h']
List_B = List_A	
List_A[0] = 20
print(List_B[0])
```

Here we set `List_B` to be equal to `List_A` and **later** changed List_A. (i.e.,after the assignment to `List_B`).   
If you are new to programming (like I was), and you are not familiar with pointers in C, you would expect the value of `List_B[0]` to remain 1. But guess what, it isn't.   
This is because while equating lists, rather than making a new list with the values of `List_A`, python just points `List_B` to the memory locations of the components of `List_A` hence, any update to `List_A` will update `List_B`. They are called references in python.   

A safe way to get around this is as follows:
```
List_A = [1,2,3,'f','g','h']
List_B = List_A	.copy() # Now instead of referencing, python will create a new list 
                        # with elements of List_A.

```

Here is a trick exercise:
```
List_A = [1,2,3,'f','g','h']
List_B = List_A	
List_A = ['p','q','r']
print(List_B)
```
What is the output of this piece of code? can you guess why?

## 2. 3-D Arrays in Numpy and how to index them?
#### a) Let us start with 2D arrays as they are simple:
Here is a simple 2D-array:

```
import numpy as np
A = np.array([[1, 2, 3],[4, 5, 6]])
print(A)
print(A.shape)
```

This will display an output which will look like this:
```
[[1 2 3]
 [4 5 6]]
(2, 3)
```
So, we have a 2X3 matrix.  
To pick a particular value (in this case let us pick '4') we have to index it as: A[1][0]  
So, the following piece of code must print 4  
```
print(A[1,0])
```
This is quite simple, as the indexing begin from 0 and from the top left corner of the matrix as shown below:   
<img src="{{ '/assets/img/2DArray.png' | prepend: site.baseurl }}" id="pimg">
*Apologies for the barbaric graphic design.*


#### b) 3D arrays:
Let us first make a 3D array.
```
import numpy as np
arr_3d = np.arange(24).reshape(3,2,4)
print(arr_3d)
```
The output of this will look something like this:
```
[[[ 0  1  2  3]
  [ 4  5  6  7]]

 [[ 8  9 10 11]
  [12 13 14 15]]

 [[16 17 18 19]
  [20 21 22 23]]]
```

This can be thought of as three 2D arrays stacked one behind the other.   
That can be shown by printing the following: 
```
print(arr_3d[0])
```
which would spurt out the following:
```
[[ 0  1  2  3]
  [ 4  5  6  7]] # compare this with the output of the entire 3D array.
```
So that means, indexing any particular element now is as simple as indexing the 2D array. Yes, it is as simple as that!

**TL;DR** - A 3D array is nothing but multiple 2D arrays stacked one behind the other. If a 3D array is denoted as (2,3,4), it means two (3,4) arrays are stacked behind each other.

> A quick exercise:    

How would you index the above 3D array to display the output [12 13 14 15]?  
Ans: print(arr_3d[1,1,:])

How to display the column [19,23]  
Ans: print(arr_3d[2,:,3])

[//]: # (Note to self: after this add a section on how to use axis while summing etc)

Ideas? comments? suggestions for improvement?
Feel free to reach me on my E-mail




