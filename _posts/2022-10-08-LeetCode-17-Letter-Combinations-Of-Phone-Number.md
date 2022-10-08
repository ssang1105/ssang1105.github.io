---
title: LeetCode 17. Letter Combinations of Phone Number
date: 2022-10-08 17:30:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Letter Combinations of Phone Number
comments: true
---

## [17. Letter Combinations of Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

## Problem

```
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.
(그림)
```

## Questions before reading example

## Example

```

Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]

Input: digits = ""
Output: []

Input: digits = "2"
Output: ["a","b","c"]
```

## Solution

* 나의 풀이

```java
class Solution {
  public List<String> letterCombinations(String digits) {
    Queue<String> queue = new LinkedList<>();
    for (char character : digits.toCharArray()) {
      if (character == '2') {
        queue.add("abc");
      } else if (character == '3') {
        queue.add("def");
      } else if (character == '4') {
        queue.add("ghi");
      } else if (character == '5') {
        queue.add("jkl");
      } else if (character == '6') {
        queue.add("mno");
      } else if (character == '7') {
        queue.add("pqrs");
      } else if (character == '8') {
        queue.add("tuv");
      } else if (character == '9') {
        queue.add("wxyz");
      }
    }
    if (queue.isEmpty()) {
      return List.of();
    }

    String first = queue.poll();
    List<String> results = first.chars()
      .mapToObj(c -> (char) c)
      .map(Object::toString)
      .toList();

    while (!queue.isEmpty()) {
      String popped = queue.poll();
      List<String> tempResults = new ArrayList<>();
      for (String currentResult : results) {
        for (char c : popped.toCharArray()) {
          tempResults.add(currentResult + c);
        }
      }
      results = tempResults;
    }

    return results;
  }
}
```
* DISCUSSION 에서 본 DFS 로 푼 풀이
``` java
 public class Solution {
    	private static final String[] KEYS = { "", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz" };

    	public List<String> letterCombinations(String digits) {
    		List<String> ret = new LinkedList<String>();
    		combination("", digits, 0, ret);
    		return ret;
    	}

    	private void combination(String prefix, String digits, int offset, List<String> ret) {
    		if (offset >= digits.length()) {
    			ret.add(prefix);
    			return;
    		}
    		String letters = KEYS[(digits.charAt(offset) - '0')];
    		for (int i = 0; i < letters.length(); i++) {
    			combination(prefix + letters.charAt(i), digits, offset + 1, ret);
    		}
    	}
    }
```

## Spent time


## Review
* 머리로는 풀이법이 떠오르지만.. 코드로 표현이 잘 되지 않아 중간에 포기할뻔도 했지만
* Queue (BFS) 를 사용하니 한번에 쉽게 풀렸다. (처음에는 DFS 를 사용하여 풀려고 했다)
* DFS 풀이법도 친숙해져야겠다..
