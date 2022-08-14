---
title: LeetCode 13. Roman To Integer
date: 2022-08-14 23:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Roman To Integer
comments: true
---

## [13. Roman To Integer](https://leetcode.com/problems/roman-to-integer/)

## Problem

```
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, 2 is written as II in Roman numeral, just two ones added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9.
X can be placed before L (50) and C (100) to make 40 and 90.
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer.
```

## Questions before reading example

// Q) Only 6 exception cases doing subtraction? // => Yes

## Example

```
Example 1:

Input: s = "III"
Output: 3
Explanation: III = 3.
Example 2:

Input: s = "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.
Example 3:

Input: s = "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.

```

## Solution

* 나의 풀이

```java
class Solution {

  public int romanToInt(String s) {
    int result = 0;
    for (int i = 0; i < s.length(); i++) {
      if (s.charAt(i) == 'I') {
        if (i < s.length() - 1) {
          if (s.charAt(i + 1) == 'V') {
            result += 4;
            i++;
            continue;
          } else if (s.charAt(i + 1) == 'X') {
            result += 9;
            i++;
            continue;
          }
        }
        result += 1;
      } else if (s.charAt(i) == 'V') {
        result += 5;
      } else if (s.charAt(i) == 'X') {
        if (i < s.length() - 1) {
          if (s.charAt(i + 1) == 'L') {
            result += 40;
            i++;
            continue;
          } else if (s.charAt(i + 1) == 'C') {
            result += 90;
            i++;
            continue;
          }
        }
        result += 10;
      } else if (s.charAt(i) == 'L') {
        result += 50;
      } else if (s.charAt(i) == 'C') {
        if (i < s.length() - 1) {
          if (s.charAt(i + 1) == 'D') {
            result += 400;
            i++;
            continue;
          } else if (s.charAt(i + 1) == 'M') {
            result += 900;
            i++;
            continue;
          }
        }
        result += 100;
      } else if (s.charAt(i) == 'D') {
        result += 500;
      } else if (s.charAt(i) == 'M') {
        result += 1000;
      }
    }

    return result;
  }

}
```
* 깔끔한 다른 풀이 (python)
```python
class Solution:
    def romanToInt(self, s: str) -> int:
        translations = {
            "I": 1,
            "V": 5,
            "X": 10,
            "L": 50,
            "C": 100,
            "D": 500,
            "M": 1000
        }
        number = 0
        s = s.replace("IV", "IIII").replace("IX", "VIIII")
        s = s.replace("XL", "XXXX").replace("XC", "LXXXX")
        s = s.replace("CD", "CCCC").replace("CM", "DCCCC")
        for char in s:
            number += translations[char]
        return number
```

## Spent time



## Review
* 오랜만에 몸풀기 문제로 가장 쉬워보이는 문제를 골랐다.
* 무식하게(?) 생각나는대로 풀었다. (물론 한번에 풀리진 않고, 중간에 실수는 있었다)
* `if - else` 문이 많은게 극혐이긴 하다..
* 미리 6가지 케이스를 replace 해서 if 문을 줄이는 방법이 아주 깔끔하고 훌륭하다.
