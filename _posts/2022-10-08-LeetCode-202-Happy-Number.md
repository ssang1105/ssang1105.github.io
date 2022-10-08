---
title: LeetCode 202. Happy Number
date: 2022-10-08 18:90:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Happy Number
comments: true
---

## [202. Happy Number](https://leetcode.com/problems/happy-number/)

## Problem

```
Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

Starting with any positive integer, replace the number by the sum of the squares of its digits.
Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
Those numbers for which this process ends in 1 are happy.
Return true if n is a happy number, and false if not.
```

## Questions before reading example
// is it possible to pass n zero?
// what is a max number of n?
// can i loop infinitely?
## Example

```
Input: n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1

Input: n = 2
Output: false
```

## Solution

* 나의 풀이

```java
class Solution {
  public boolean isHappy(int n) {
    Set<String> seen = new HashSet<>();
    String numberString = String.valueOf(n);
    seen.add(numberString);
    while (true) {
      int sum = 0;
      for (char c: numberString.toCharArray()) {
        sum += (c - '0') * (c - '0');
      }
      numberString = String.valueOf(sum);
      if (seen.contains(numberString)) {
        break;
      } else {
        seen.add(numberString);
      }
    }

    return numberString.equals("1");
  }
}
```


## Spent time
* 20m

## Review
* 무한 루프 탈출 조건에 대해 생각해내기 어려웠다. (단순히 length 가 2이상이면 탈출 조건으로 했었다)
* "7이 왜 unhappy 한 number 이지" 고민하다가, solution 을 보고 cycle 이 생긴다는 것을 알아내어 Set 을 사용하여 해결했다.
