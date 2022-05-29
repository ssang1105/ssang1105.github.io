---
title: LeetCode 937. Reorder Data in Log Files
date: 2022-05-29 10:30:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Reorder Data in Log Files
comments: true
---

## [397. Reorder Data in Log Files](https://leetcode.com/problems/reorder-data-in-log-files/)

## Problem

```
You are given an array of logs. Each log is a space-delimited string of words, where the first word is the identifier.

There are two types of logs:

Letter-logs: All words (except the identifier) consist of lowercase English letters.
Digit-logs: All words (except the identifier) consist of digits.
Reorder these logs so that:

The letter-logs come before all digit-logs.
The letter-logs are sorted lexicographically by their contents. If their contents are the same, then sort them lexicographically by their identifiers.
The digit-logs maintain their relative ordering.
Return the final order of the logs.

```

## Questions before reading example
// Q)
// 1. identifier with empty is available?
// => nope
// 2. all words have identifier ?
// => yeap
// 3. what is a identifier?
// => the word whicch has a specific rule
// 4. any other exceptional case? uppercase words, other words..
// => maybe


## Example

```
Input: logs = ["dig1 8 1 5 1","let1 art can","dig2 3 6","let2 own kit dig","let3 art zero"]
Output: ["let1 art can","let3 art zero","let2 own kit dig","dig1 8 1 5 1","dig2 3 6"]
Explanation:
The letter-log contents are all different, so their ordering is "art can", "art zero", "own kit dig".
The digit-logs have a relative order of "dig1 8 1 5 1", "dig2 3 6".


Input: logs = ["a1 9 2 3 1","g1 act car","zo4 4 7","ab1 off key dog","a8 act zoo"]
Output: ["g1 act car","a8 act zoo","ab1 off key dog","a1 9 2 3 1","zo4 4 7"]
```

## Solution

* Discussion 을 참고한 나의 풀이

```java
class Solution {
  public String[] reorderLogFiles(String[] logs) {
    List<String> letterLogs = new ArrayList<>();
    List<String> digitLogs = new ArrayList<>();
    for (String log : logs) {
      if (isDigit(log.charAt(log.length() - 1))) {
        digitLogs.add(log);
      } else {
        letterLogs.add(log);
      }
    }

    List<String> sortedLetterLogs = letterLogs.stream()
      .sorted(Comparator.comparing((String log) -> {
        String identifier = log.split(" ")[0];
        return log.substring(identifier.length());
      }).thenComparing((String log) -> {
        String identifier = log.split(" ")[0];
        return identifier;
      }))
      .collect(Collectors.toList());

    sortedLetterLogs.addAll(digitLogs);
    return sortedLetterLogs.toArray(String[]::new);
  }

  private static boolean isDigit(Character character) {
    return (int) character >= 48 && (int) character <= 57;
  }

}
```

## Spent time

* 1시간 30분..?

## Review
* 문제를 제대로 읽지 못해서 한참 헤매였다.
* 코너 케이스를 제대로 파악하지 못하였다.
* 처음에는 Map 으로 풀려고 했다. (이것도 한참 걸렸다..)
  * 그런데 Key (identifier) 가 중복이 되는 CASE 가 있어서 포기했다.
* Discussion 을 보니.. 이것 이외에도 문제를 잘못읽은 부분이 있었다.
* 크게 digits 과 letters 를 분류, (이 과정에서 처음에 input String 을 그대로 관리하면 됐는데, 이를 또 쪼개려 했다)
* letters sorting (이 과정에서 contents 가 같으면 identifier 를 비교해야하는것도 놓쳤다.)
* 두가지만 잘하면 쉽게 풀리는 문제인데.. 너무 헤맸다.
* 아직 많이 부족하다..
