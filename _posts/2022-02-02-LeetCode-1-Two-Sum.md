---
layout: post
title: LeetCode : 1. Two Sum 
categories: [leetcode, algorithm]
tags: [algorithm]
description : Two Sum comments: true
---

## Problem

```
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.
```

## Questions before reading example

* "nums" 가 비어있을 수도 있는가?
* "nums" 의 최대 길이는?
* "nums" 의 element 와 target 은 항상 int 타입인가?
* "nums" 의 element 와 target 은 항상 양수인가?
* 시간복잡도가 n^2 이어도 괜찮은가?

## Example

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

## Solution

* O(n^2)

```java
  public int[]twoSum(int[]nums,int target){
    for(int i=0;i<nums.length;i++){
    for(int j=i+1;j<nums.length;j++){
    if(nums[i]+nums[j]==target){
    return new int[]{i,j};
    }
    }
    }
    return null;
    }
```

* O(n)

```java
  public static int[]twoSum(int[]nums,int target){
    Map<Integer, Integer> map=new HashMap<>();
    for(int i=0;i<nums.length;i++){
    int remainder=target-nums[i];
    if(map.containsKey(remainder)){
    return new int[]{map.get(remainder),i};
    }
    map.put(nums[i],i);
    }
    throw new IllegalArgumentException();
    }
```

## Time spent

* 9분

## Review

* 정말 오랜만에 풀어보았다.
* O(n) 풀이법은 스스로 생각하지 못해 검색을 통해 해결했다.
* 매일 꾸준히 연습해야지

## LeetCode
* [1 : Two Sum](https://leetcode.com/problems/two-sum)