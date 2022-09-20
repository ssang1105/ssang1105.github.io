---
title: LeetCode 118. Pascal's Triangle
date: 2022-09-19 00:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Pascal's Triangle
comments: true
---

## [118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)

## Problem

```
Given an integer numRows, return the first numRows of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:
(그림)
```

## Questions before reading example

## Example

```
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]

Input: numRows = 1
Output: [[1]]
```

## Solution

* 나의 풀이

```java
class Solution {
  public List<List<Integer>> generate(int numRows) {
    List<List<Integer>> results = new ArrayList<>();
    results.add(List.of(1));
    if (numRows == 1) {
      return results;
    }
    results.add(List.of(1, 1));
    if (numRows == 2) {
      return results;
    }

    for (int i = 2; i < numRows; i++) {
      List<Integer> previousRow = results.get(i - 1);
      List<Integer> newRow = new ArrayList<>();
      newRow.add(1);
      for (int j = 1; j < previousRow.size(); j++) {
        newRow.add(previousRow.get(j-1) + previousRow.get(j));
      }
      newRow.add(1);
      results.add(newRow);
    }

    return results;
  }
}
```


## Spent time


## Review
* Easy 난이도여서 그런지 무식하게 푸니 풀렸다.
