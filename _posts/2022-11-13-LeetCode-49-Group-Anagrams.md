---
title: LeetCode 48. Group Anagrams
date: 2022-11-13 00:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Group Anagrams
comments: true
---

## [48. Group Anagrams](https://leetcode.com/problems/group-anagrams/)

## Problem

```
Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

```

## Questions before reading example

## Example

```
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]

Input: strs = [""]
Output: [[""]]

Input: strs = ["a"]
Output: [["a"]]
```

## Solution

* 나의 풀이

```java
  class Solution {
  public List<List<String>> groupAnagrams(String[] strs) {
    Map<String, List<String>> inspectionMap = new HashMap<>();
    for (String input : strs) {
      char[] inputChars = input.toCharArray();
      Arrays.sort(inputChars);
      String key = String.valueOf(inputChars);
      if (inspectionMap.get(key) == null) {
        List<String> arrayList = new ArrayList<>();
        arrayList.add(input);
        inspectionMap.put(key, arrayList);
      } else {
        List<String> oldList = inspectionMap.get(key);
        oldList.add(input);
      }
    }

    return inspectionMap.values().stream().toList();
  }
}
```

## Spent time
* 20m

## Review
* 처음에는 1) 글자수로 grouping, 2) 글자의 합으로 grouping 하여 풀이를 시도하였다. (Example 전부 PASS)
* 하지만 글자수가 같으면서도 글자의 합이 같은 CASE 에서 실패했고.. discussion 살짝 보고 정렬 + map 힌트를 얻어서 풀었다.
