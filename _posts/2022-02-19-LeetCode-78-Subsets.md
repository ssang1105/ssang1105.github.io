---
title: LeetCode 78. Subsets
date: 2022-02-19 16:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Subsets
comments: true
---

## [78. Subsets](https://leetcode.com/problems/subsets/)

## Problem

```
Given an integer array nums of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

```

## Questions before reading example
* nums empty?
* min/max length? unique?
* empty subset?

## Example

```
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]

Input: nums = [0]
Output: [[],[0]]
```

## Solution
* 나의 풀이
```java
class Solution {

  public List<List<Integer>> subsets(int[] nums) {

    List<List<Integer>> results = new ArrayList<>();
    backtracking(nums, new ArrayList<>(), results, 0);
    return results;
  }

  private void backtracking(int[] nums, List<Integer> candidates, List<List<Integer>> results, int start) {
    results.add(new ArrayList<>(candidates));
    for (int i = start; i < nums.length; i++) {
      candidates.add(nums[i]);
      backtracking(nums, candidates, results, i + 1);
      candidates.remove(candidates.size() - 1);
    }


  }
}
```


## Spent time


## Review

* 46 Permutations 에 이어 연속적으로 풀어본 백트래킹 문제
* 풀이법이 거의 비슷하다
* 주요 포인트는 `results.add(new ArrayList<>(candidates));`
