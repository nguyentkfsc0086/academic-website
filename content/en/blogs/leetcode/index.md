---
title: Random leetcode
date: 2025-12-09
type: post
tags:
    - personal
---
### 66. Plus One
You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's. \

Increment the large integer by one and return the resulting array of digits.

```python
class Solution(object):
    def plusOne(self, digits):
        number_string = ''
        for i in range(0, len(digits)):
            number_string = number_string + str(digits[i])
        number = int(number_string) + 1
        number_hjhj = str(number)
        result = []
        for i in range(0, len(number_hjhj)):
            result.append(int(number_hjhj[i]))
        return result
```