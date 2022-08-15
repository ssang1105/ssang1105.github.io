---
title: LeetCode 14. Longest Common Prefix
date: 2022-08-15 23:30:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Longest Common Prefix
comments: true
---

## [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)

## Problem

```
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".
```

## Questions before reading example

// Q) Only 6 exception cases doing subtraction? // => Yes

## Example

```
Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.

```

## Solution

* 나의 풀이

```java
class Solution {
  public String longestCommonPrefix(String[] strs) {
    String result = "";

    String standard = strs[0];
    for (int i = 0; i < standard.length(); i++) {
      char standardChar = standard.charAt(i);
      boolean isSame = false;
      for (int j = 0; j < strs.length; j++) {
        if (strs[j].length() <= i) {
          break;
        }
        if (strs[j].charAt(i) == standardChar) {
          isSame = true;
        } else {
          isSame = false;
          break;
        }

        if (j == strs.length -1) {
          result += standardChar;
        }
      }
      if (!isSame) {
        break;
      }
    }
    return result;
  }
}
```


## Spent time



## Review
* 보자마자 정말 쉬운 문제라고 생각했는데.. 생각보다 문제해결 방법을 코드로 구현하는데에 시간이 걸렸다.
* 자신이 있는 나머지 문제 풀기전에 예외 케이스에 대한 질문거리를 남기지 않았는데, 이게 독이 되었다
  * 예외 케이스에 대한 코드 (ex. input 이 1개인 경우, 첫번째 input 의 길이가 짧은 경우 ..) 에 대해 고려를 하지 않아서 if 문이 덕지덕지 붙었다.
