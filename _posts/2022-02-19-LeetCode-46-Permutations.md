---
title: LeetCode 46. Permutations
date: 2022-02-19 14:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Permutations
comments: true
---

## [46. Permutations](https://leetcode.com/problems/permutations/)

## Problem

```
Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

```

## Questions before reading example


## Example

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

Input: nums = [0,1]
Output: [[0,1],[1,0]]

Input: nums = [1]
Output: [[1]]
```

## Solution
* 나의 풀이
```java
class Solution {

  int[] visited;

  public List<List<Integer>> permute(int[] nums) {
    visited = new int[nums.length];

    List<List<Integer>> results = new ArrayList<>();

    dfs(nums, new ArrayList<>(), results);
    return results;
  }

  private void dfs(int[] nums, List<Integer> candidates, List<List<Integer>> results) {
    if (candidates.size() == nums.length) {
      results.add(new ArrayList<>(candidates));
      return;
    }

    for (int i = 0; i < nums.length; i++) {
      if (visited[i] == 1) {
        continue;
      }

      visited[i] = 1;
      candidates.add(nums[i]);
      dfs(nums, candidates, results);
      candidates.remove(candidates.size() - 1);
      visited[i] = 0;
    }

  }

}
```

* 다른 풀이 (`백트래킹` + `리스트 contains`)

```java
public List<List<Integer>> permute(int[] nums) {
   List<List<Integer>> list = new ArrayList<>();
   // Arrays.sort(nums); // not necessary
   backtrack(list, new ArrayList<>(), nums);
   return list;
}

private void backtrack(List<List<Integer>> list, List<Integer> tempList, int [] nums){
   if(tempList.size() == nums.length){
      list.add(new ArrayList<>(tempList));
   } else{
      for(int i = 0; i < nums.length; i++){
         if(tempList.contains(nums[i])) continue; // element already exists, skip
         tempList.add(nums[i]);
         backtrack(list, tempList, nums);
         tempList.remove(tempList.size() - 1);
      }
   }
}
```

## Spent time


## Review

* 기본적인 "순열" 문제. visited 라는 아이디어는 떠올렸지만, 한번에 풀지 못하고 다른 풀이를 참고했다..
* `백트래킹`
