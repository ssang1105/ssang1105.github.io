---
title: LeetCode 104. Maximum Depth Of Binary Tree
date: 2022-02-06 21:00:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Maximum Depth Of Binary Tree
comments: true
---

## [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)

## Problem

```
Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.
```

## Questions before reading example

1. `DFS` vs BFS
  * DFS 가 더 구현이 쉽기 때문에 DFS

## Example

```
Input: root = [3,9,20,null,null,15,7]
Output: 3

Input: root = [1,null,2]
Output: 2
```

## Solution

```java
  class Solution {
  public int maxDepth(TreeNode root) {
    return dfs(root, 0);
  }

  private int dfs(TreeNode node, int currentDepth) {
    if (node == null) {
      return currentDepth;
    }

    return Math.max(dfs(node.left, currentDepth +1), dfs(node.right, currentDepth + 1));
  }
}
```

## Spent time


## Review

* DFS 기본 문제인데.. 문제해결에 시간이 생각보다 걸렸다.

