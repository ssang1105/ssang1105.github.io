---
title: LeetCode 412. FizzBuzz
date: 2022-02-13 22:30:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : N-ary Tree Level Order Traversal
comments: true
---

## [429. N-ary Tree Level Order Traversal](https://leetcode.com/problems/n-ary-tree-level-order-traversal/)

## Problem

```
Given an n-ary tree, return the level order traversal of its nodes' values.

Nary-Tree input serialization is represented in their level order traversal, each group of children is separated by the null value (See examples).

```

## Questions before reading example


## Example

```
Input: root = [1,null,3,2,4,null,5,6]
Output: [[1],[3,2,4],[5,6]]

Input: root = [1,null,2,3,4,5,null,null,6,7,null,8,null,9,10,null,null,11,null,12,null,13,null,null,14]
Output: [[1],[2,3,4,5],[6,7,8,9,10],[11,12,13],[14]]
```

## Solution

```java
class Solution {
  public List<List<Integer>> levelOrder(Node root) {
    List<List<Integer>> result = new ArrayList<>();
    if (root == null) {
      return result;
    }

    Queue<Node> queue = new LinkedList<>();
    queue.add(root);

    while (!queue.isEmpty()) {
      List<Integer> nLevelValues = new ArrayList<>();
      int size = queue.size();
      for (int i = 0; i < size; i++) {
        nLevelValues.add(queue.peek().val);
        queue.addAll(queue.poll().children);
      }
      result.add(nLevelValues);
    }

    return result;
  }
}
```

## Spent time


## Review

* tree 가 나오면 dfs/bfs 부터 생각은 하지만 무얼 써야할지는 잘 떠오르지 않는다.
* 아직 dfs/bfs 문제 풀이가 낯설다.. 스스로 온전히 해내기 어렵다.
* 많이 풀어보는 수 밖에..
