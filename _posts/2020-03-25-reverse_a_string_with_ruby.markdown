---
layout: post
title:      "Reverse a String with Ruby"
date:       2020-03-26 00:33:13 +0000
permalink:  reverse_a_string_with_ruby
---


So, this question came up during a recent in person technical interview . I had been practicing the Top Easy Interview question a couple weeks prior and this was one of the questions on the list which felt so awesome. There are many ways to solve this but I like to use the two pointer method. 

The problem...

```
Write a function that reverses a string. The input string is given as an array of characters char[].

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

You may assume all the characters consist of printable ascii characters.
```

Example 1

```
Input: ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```

Example 2

```
Input: ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```



First, lets set up our left and right pointers that point to the beginning and end of the string.

```
def reverse_string(s)
    left = 0
    right = s.size - 1
end
```

Next, we will loop through the array until the pointers meet in the middle.

```
def reverse_string(s)
    left = 0
    right = s.size - 1
    
    while left < right do 
    
    end
end
```

Finally, on every iteration we will set the left pointer to the right pointer swapping the values from the left side of the array to the right side. With other languages you most likely will have to set the left side to a temporary variable so you can store the value after it's replaced with the value on the right side. Ruby makes this step really easy letting us do it on one line. Then we can increment the left pointer and decrement the right pointer, moving them close 1 step closer. 

```
def reverse_string(s)
    left = 0
    right = s.size - 1
    
    while left < right do 
        s[left], s[right] = s[right], s[left]
        
        left += 1
        right -= 1
    end
end
```

I have noticed that most companies use string type algorithm problems in their interview process, so it's definitely something you should pay some attention to. It feels great when you walk into an interview and have already seen the question they are asking. 










