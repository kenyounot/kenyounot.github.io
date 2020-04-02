---
layout: post
title:      "Single Number in Python"
date:       2020-04-02 01:00:36 -0400
permalink:  single_number_in_python
---

I started the Leetcode's 30 days of code challenge. The first problem was to find the single element that doesn't appear twice in the array.

The first thing we want to do is think about which data structure we want to use. I chose a hash because we can set the num value as the key and the frequency the num appears in the array to the value. 

```
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        num_hash = {}
```

Next, let's iterate over the array checking if the num exists in the hash, if it does, increment by one, if it doesn't then add the num as a key and set the value to one.

```
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        num_hash = {}
        
        for i in nums:
            if i in num_hash:
                num_hash[i] +=1
            else:
                num_hash[i] = 1
```

Now that we have our hash populated with the values we can now iterate over the hash and check which num has a value of only one and then return the key.

```
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        num_hash = {}
        
        for i in nums:
            if i in num_hash:
                num_hash[i] +=1
            else:
                num_hash[i] = 1
        
        
        for key in num_hash:
            if num_hash[key] == 1:
                return key
```

And there we go, clean working solution that can be used on a wide array of different problems.






