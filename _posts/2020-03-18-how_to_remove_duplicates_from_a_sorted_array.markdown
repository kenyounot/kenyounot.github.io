---
layout: post
title:      "How to Remove Duplicates From a Sorted Array"
date:       2020-03-19 01:49:47 +0000
permalink:  how_to_remove_duplicates_from_a_sorted_array
---


I've been working on improving my computer science skills and algorithmic ability through sources like leetcode to prepare for interviews. As someone who hasn't had a traditional computer science education path this preperation has definitely been the hardest for me. Alot of people say blogging helps to solidify your knowledge of things youre learning about so I will use this to teach while also strengethening my skills. I'm going to use Golang to solve these problems, I noticed there isn't many resources for solving these common algorithms with Golang, and I love Go so it was an obvious choice. 

So, lets move on to our first problem ...
```
Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

```
**  Example 1**

```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

```
** Example 2 **


```
Given nums = [0,0,1,1,1,2,2,3,3,4],

Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.

It doesn't matter what values are set beyond the returned length.

It doesn't matter what you leave beyond the returned length.
```

Okay, so what do we know, the first important thing to note is that the array is **sorted**, that's important because if a number has any duplicates it's going to be immediatley to the right of the index you're on. The next thing we need to note is that in order to modify this array in place we need to keep track of where we are going to place the next unique value. This will be explained more when the problem is written out.  We also know that the first number in the array is always going to be unique, so we shouldn't do anything with that first digit. 

```
// we start with a function that takes in an array of integers and returns an integer
func removeDuplicates(nums []int) int {
    // set the index of where we place the next unique value, we start at 1 because the 0 index will always be unique
		index := 1
		
		// set length of the array
		arrayLen := len(nums)
		
		// loop through the nums array, set arrayLen -1 so we dont go out of bounds
		for i:=0; i < arrayLen - 1; i++ {
		
	    // if current num isn't equal to the next number, set the next num to the current index
        if nums[i] != nums[i+1] {
            nums[index] = nums[i+1]
						
		//increment the index
            index++
        }
    }
    
		// this holds the index of all the unique characts
    return index;
		
		
}
```

This solution beats 99.74% of all other solutions and it's very simple with minimal lines of code. See you on the next problem. 

