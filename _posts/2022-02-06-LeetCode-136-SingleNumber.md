---
title: LeetCode 136. Single Number
date: 2022-02-06 21:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Single Number
comments: true
---

## [136. Single Number](https://leetcode.com/problems/single-number/)

## Problem

```
Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.
```

## Questions before reading example
* only constant extra space 인데 Map 을 사용해도 될까?
* 최악의 경우 O(n) 을 사용할텐데..


## Example

```
Input: nums = [2,2,1]
Output: 1

Input: nums = [4,1,2,1,2]
Output: 4

Input: nums = [1]
Output: 1
```

## Solution

* 나의 풀이
```java
class Solution {
  public int singleNumber(int[] nums) {

    Map<Integer, Boolean> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
      if (map.containsKey(nums[i])) {
        map.put(nums[i], false);
      } else {
        map.put(nums[i], true);
      }
    }
    return map.entrySet().stream()
      .filter(Entry::getValue)
      .map(Entry::getKey)
      .findFirst().orElseThrow();

  }
}
```

* XOR 를 사용한 풀이
```java
class Solution {
  public int singleNumber(int[] nums) {
    int ans = 0;
    for (int i = 0; i < nums.length; i++) {
      ans ^= nums[i];
    }
    return ans;
  }
}
```
## Spent time

## Review

* constant extra space 제약 조건 때문에 다른 아이디어가 없을지 고민을 꽤했지만 떠오르지 않아서 Map 으로 풀었다. (운이 좋게 PASS 한 것 같다)
* 다른 문제 풀이를 보니 `XOR` 를 이용해서 비트 연산으로 푸는거였다.
  * XOR 는 같으면 0 다르면 1을 반환한다.



