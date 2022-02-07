---
title: LeetCode 412. FizzBuzz
date: 2022-02-07 22:30:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : FizzBuzz
comments: true
---

## [412. Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)

## Problem

```
Given an integer n, return a string array answer (1-indexed) where:

answer[i] == "FizzBuzz" if i is divisible by 3 and 5.
answer[i] == "Fizz" if i is divisible by 3.
answer[i] == "Buzz" if i is divisible by 5.
answer[i] == i (as a string) if none of the above conditions are true.
```

## Questions before reading example
1. n always posivie? yes

## Example

```
Input: n = 3
Output: ["1","2","Fizz"]

Input: n = 5
Output: ["1","2","Fizz","4","Buzz"]

Input: n = 15
Output: ["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]
```

## Solution

```java
class Solution {
  public List<String> fizzBuzz(int n) {
    List<String> results = new LinkedList<>();
    for (int i = 1; i <= n; i++) {
      if (i % 3 == 0 && i % 5 == 0) {
        results.add("FizzBuzz");
      } else if (i % 3 == 0) {
        results.add("Fizz");
      } else if (i % 5 == 0) {
        results.add("Buzz");
      } else {
        results.add(String.valueOf(i));
      }
    }
    return results;

  }
}
```

## Spent time
* 5분

## Review

* 이런 문제가 실제 면접에 나오면 소원이 없겠다..
