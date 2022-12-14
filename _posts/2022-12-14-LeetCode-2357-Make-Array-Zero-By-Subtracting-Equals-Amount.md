---
title: 2357. Make Array Zero by Subtracting Equal Amounts
date: 2022-12-14 22:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Make Array Zero by Subtracting Equal Amounts
comments: true
---

## [2357. Make Array Zero by Subtracting Equal Amounts](https://leetcode.com/problems/make-array-zero-by-subtracting-equal-amounts/)

## [Problem & Example](https://github.com/ssang1105/LeetCode/tree/master/2357-make-array-zero-by-subtracting-equal-amounts)


## Questions before reading example

## [나의 풀이](https://github.com/ssang1105/LeetCode/blob/master/2357-make-array-zero-by-subtracting-equal-amounts/2357-make-array-zero-by-subtracting-equal-amounts.java)
### time complexity : O(n^2)
### space complexity : O(1)

## 다른 풀이 (SIMPLE, EASY-UNDERSTANDING)
```java
class Solution {
  public int minimumOperations(int[] nums) {
    HashSet<Integer> set = new HashSet<>();
    for(int a : nums) {
      if(a > 0)
        set.add(a);
    }
    return set.size();
  }
}
```
## Spent time
* 5m

## Review
* 문제 그대로 brute force 하게 풀었다.
* 하지만.. 문제를 깊이 이해하고 나면, Set 으로 한방에 풀 수 있다는 걸 알 수 있다. (물론 나도 discussion 을 보고 알았다)
* 낮은 수부터 빼고, 중복숫자 빼고..
