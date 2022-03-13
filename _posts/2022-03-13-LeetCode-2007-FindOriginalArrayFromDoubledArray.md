---
title: LeetCode 2007. Find Original Array From Doubled Array
date: 2022-03-13 21:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Find Original Array From Doubled Array
comments: true
---

## [2007. Find Original Array From Doubled Array](https://leetcode.com/problems/find-original-array-from-doubled-array/)

## Problem

```
An integer array original is transformed into a doubled array changed by appending twice the value of every element in original, and then randomly shuffling the resulting array.

Given an array changed, return original if changed is a doubled array. If changed is not a doubled array, return an empty array. The elements in original may be returned in any order.

```

## Questions before reading example

## Example

```
Input: changed = [1,3,4,2,6,8]
Output: [1,3,4]
Explanation: One possible original array could be [1,3,4]:
- Twice the value of 1 is 1 * 2 = 2.
- Twice the value of 3 is 3 * 2 = 6.
- Twice the value of 4 is 4 * 2 = 8.
Other original arrays could be [4,3,1] or [3,1,4].

Input: changed = [6,3,0,1]
Output: []
Explanation: changed is not a doubled array.

Input: changed = [1]
Output: []
Explanation: changed is not a doubled array.
```

## Solution

* Discussion 을 참고한 나의 풀이

```java
class Solution {
  public int[] findOriginalArray(int[] changed) {

    if (changed.length % 2 != 0) {
      return new int[0];
    }
    Arrays.sort(changed);
    Map<Integer, Integer> map = new HashMap<>();
    int[] results = new int[changed.length / 2];
    int index = 0;
    for (int i = changed.length - 1; i >= 0; i--) {
      int twice = changed[i] * 2;
      if (map.containsKey(twice)) {
        if (map.get(twice) == 1) {
          map.remove(twice);
        } else {
          map.put(twice, map.get(twice) - 1);
        }
        results[index++] = changed[i];
      } else {
        map.put(changed[i], map.getOrDefault(changed[i], 0) + 1);
      }
    }
    return index == changed.length / 2 ? results : new int[]{};
  }
}
```

## Spent time

* 40분

## Review
* 보자 마자 Map 을 잘 활용하면 되겠구나 싶어서 바로 풀이에 들어갔는데.. 역시나 실패했다.
* 아래 내용들이 실패의 원인이고, Discussion 을 보며 결국 풀 수 있었다.
  1. twice 한 숫자가 Doubled Array 후보가 되는 경우를 잡아내기
  2. map 으로 처리 후 결과를 위해 연산하는게 아니라 result 배열을 선언해서 한번에 결과 도출하기
     1. index..
  3. 갯수가 홀수개인 경우 바로 제외 시키기.
