---
title: LeetCode 9. Palindrome Number
date: 2022-11-14 00:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Palindrome Number
comments: true
---

## [9. Palindrome Number](https://leetcode.com/problems/palindrome-number/)

## [Problem & Example](https://github.com/ssang1105/LeetCode/tree/master/0009-palindrome-number)


## Questions before reading example

## Solution

* 나의 풀이

```java
class Solution {

  public boolean isPalindrome(int x) {
    if (x < 0) {
      return false;
    }

    String xStr = String.valueOf(x);
    for (int i = 0; i < xStr.length() / 2; i++) {
      if (xStr.charAt(i) != xStr.charAt(xStr.length() - i - 1)) {
        return false;
      }
    }

    return true;
  }
}
```

## Spent time
* 5m

## Review
* 예전에 분명히 풀어보았던 팰린드롬의 수 문제
* 함정이 있을까 조마조마하며 풀었는데 다행히 한번에 잘 풀렸다.
