---
title: LeetCode 344. Reverse String
date: 2022-02-06 20:30:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Reverse String
comments: true
---

## [344. Reverse String](https://leetcode.com/problems/reverse-string/)

## Problem

```
Write a function that reverses a string. The input string is given as an array of characters s.

You must do this by modifying the input array in-place with O(1) extra memory.
```

## Questions before reading example
1. "s" can be empty? nope
2. "s" max length? 10^5
3. "s" only english? yes

## Example

```
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]

Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

## Solution

```java
class Solution {
  public void reverseString(char[] s) {
    for (int i = 0; i < s.length / 2; i++) {
      char tmp = s[i];
      s[i] = s[s.length - 1 - i];
      s[s.length - 1 - i] = tmp;
    }

  }
}
```

## Spent time
* 13분

## Review

* 생각나는 그대로 풀었는데 다행히 잘 풀렸다.
* index 를 다루는건 늘 조심스럽다.

