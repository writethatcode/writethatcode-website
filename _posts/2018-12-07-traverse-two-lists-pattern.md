---
layout: post
title:  "Merge two sorted arrays interview pattern"
author: sal
categories: [ codinginterview ]
image: assets/images/16.jpg
permalink: merge-two-lists-pattern
---

**The last thing I want you to do in a coding interview is to think.**  

Seriously, Let me explain, there are many ready made patterns which you can apply immediately in a coding interview that will save you a huge amount of problem and thinking.  In fact unless you want to solve hundreds of problems you should get those patterns right.  

This is why we introduce all these patterns.  This coding interview pattern deals with something that sounds so simple yet, it has it's own obstacles.  

You don't want to face these obstacles while in a coding interview.  Below is the task and the internal patterns.

Don't take the question below not seriously it's about merging two sorted arrays, we must understand the basics until we feel perfect with it and can inscribe it in the middle of night if woken up.  We build on these basics for more complex questions.

> Note: all examples and reference is in java.

## Our Steps

1. Step 1: Ask questions
1. Step 2: The task: Merge two sorted arrays 
1. Step 3: The new array's length
1. Step 4: Create the output array
1. Step 5: Initialize pointers.
1. Step 6: Traverse the arrays choose the smaller number
1. Step 7: We didn't finish only one of the input arrays have reached the end.
1. Step 8: Array merge pattern recap


## Step 1: Ask questions

Question 1: Whenever we deal with arrays with numbers and sorting, ask the following question: can it contain duplicates?

- Don't fear that these questions can increase the question difficulty, the interviewer already has the question in mind, if you don't ask he would put that as a new obstacle.

Question 2: Can we change the arrays?
- Note that changing the input's is a pattern of itse'f and can help you in many times, but we'll discuss it in another post.  The answer can be obviously yes/no, we would go with the `no` thus our output space complexity would be `O(n)` as we are planning on creating a whole new array with the result.

## Step 2: The task: Merge two sorted arrays

Here is the question from one of the popular coding interview questions sites, merge the below two sorted arrays.

The method signagure:

`public int[] mergeTwoArrays(int[] nums1, int[] nums2)`

When looking at this signature we understand the following:

1. It accepts two arrays `nums1`, `nums2` each of type `int[]` an array of numbers.
1. It returns a new array containing the merged arrays with type `int[]`

## Step 3: The new array's length

The resulting array length is the sum of the two array's length, and in our case it's: `nums1.length` + `nums2.length`

> Tip: Remember in java arrays length is without brackets: `length` while list length is with brackets and also has a different name it's `size()`

- Array size: `length`
- List size: `size()`

## Step 4: Create the output array

Prepare the output array, we are going to create a new array, it's size is going to be the sum of the size of the two input arrays as we said here it is, our output array:

`int[] merged = new int[num1.length + nums2.length];`

Rather easy, we have just created our merged array and it's length is the combined length of the two input arrays.

## Step 5: Initialize pointers.

In this step we are going to initialize 3 pointers:

1. Output array pointer: `k`
1. Input1 array pointer: `i`
1. Input2 array pointer: `j`

In java we can do this in one line:

```java
int i = 0, j = 0, k = 0;
```

## Step 6: Traverse the arrays choose the smaller number

1. Use a while loop
1. While we didn't reach any of the input arrays end
1. Choose the smaller number and put in the output array
1. When you take a number from input array and place on the output array increment that very same input array index.

```java
    while (i < nums1.length && j < nums2.length) { // While we didn't reach any of the input arrays end.
        arr[k++] = nums1[i] < nums2[j] ? nums1[i++] : nums2[j++]; // Take the smaller, put on output array increment that input array pointer.
    }
```

## Step 7: We didn't finish only one of the input arrays have reached the end.

OK, this was a basically one liner in a `while` loop to merge both arrays.  But as you see in the condition: `(i < nums1.length && j < nums2.length)` it's obvious that one array would reach the end before the other, therefore we now need to take the other array, the one that did not reach the end and simply traverse it all until the end and for each item add it to the merged output array until the end that's it.

1. Check which input array did not reach it's end.
1. Just go through this input array and dump all items into the output array.

> Pattern: **while is practically if + loop** So whenever you need to use an `if` and then `while` check if you could just use a `while`, this will make your code more compact and simpler for you to write read and analyze.


```java
    while (i < nums1.length) arr[k++] = nums1[i++];
    while (j < nums2.length) arr[k++] = nums2[j++];
```

You see in the above code we have our while do two things:

1. `while (i < nums1.length)` : first while job: check if we have reached the array end.
1. `while (i < nums1.length)` : second while job: traverse the array until the end.

and for each such item in the array we just put it in the output array `arr[k++]` and we incremet the index that's it.

lastly we just return the output array which contains the result `return arr`.

## Step 8: Array merge pattern recap

1. Create output array (sum of input arr lengths)
1. Use `while` and choose smallest value put in output array.
1. Job is not done we have reached only one of the arrays end, use `while` to traverse both array separately until the end without comparison and put in result array.