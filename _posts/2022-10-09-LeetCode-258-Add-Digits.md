---
title: LeetCode 258. Add Digits
date: 2022-10-10 00:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Add Digits
comments: true
---

## [258. Add Digits](https://leetcode.com/problems/add-digits/)

## Problem

```
Given an integer num, repeatedly add all its digits until the result has only one digit, and return it.

```

## Questions before reading example

## Example

```
Input: num = 38
Output: 2
Explanation: The process is
38 --> 3 + 8 --> 11
11 --> 1 + 1 --> 2
Since 2 has only one digit, return it.
```

## Solution

* 나의 풀이

```java
class Solution {
  public int addDigits(int num) {
    String numString = String.valueOf(num);

    while (numString.length() > 1) {
      int sum = 0;
      for (char c : numString.toCharArray()) {
        sum += c - '0';
      }
      numString = String.valueOf(sum);
    }

    return Integer.parseInt(numString);
  }
}
```
* 재귀로 푼 풀이
```java
class Solution {

  public int sumDigits(int n) {
    if (n == 0)
      return 0;
    return (n % 10) + sumDigits(n / 10);
  }
}
```
## Spent time
* 5m

## Review
* HappyNumber 와 같은 방법으로 풀었다.
* 재귀로도 문제를 깔끔하게 풀 수 있는데.. 이 방법에 더 익숙해지고 싶다.
