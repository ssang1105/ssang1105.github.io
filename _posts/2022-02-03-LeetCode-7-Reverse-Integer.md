---
title: LeetCode-Reverse Integer
date: 2022-02-03 22:00:00 +0800
categories: [leetcode, algorithm]
tags: [algorithm]
description : Reverse Integer
comments: true
---

## [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)

## Problem

```
Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).
```

## Questions before reading example

1. (memo) negative case
2. (memo) ends with zero case

## Example

```
Input: x = 123
Output: 321

Input: x = -123
Output: -321

Input: x = 120
Output: 21
```

## Solution

* Character 와 Stack 을 사용한 `나의` 풀이

```java
  public int reverse(int x) {
    String s = String.valueOf(x);
    Stack<Character> stack = new Stack<>();
    boolean isPositive = true;
    for (int i = 0; i < s.length(); i++) {
      if (s.charAt(i) == '-') {
        isPositive = false;
        continue;
      }
      stack.push(s.charAt(i));
    }

    StringBuilder resultStringBuilder = new StringBuilder();
    if (!isPositive) {
      resultStringBuilder.append("-");
    }
    while (!stack.empty()) {
      resultStringBuilder.append(stack.pop());
    }

    long result = Long.parseLong(resultStringBuilder.toString());
    if (result > Integer.MAX_VALUE || result < Integer.MIN_VALUE) {
      return 0;
    }

    return (int) result;
  }
```

* `*(곱셈)`과 `%(Arithmetic Operators)` 를 사용한 long -> int 아이디어

``` java
  public int reverse(int x) {
      long num = 0;
      while (x != 0) {
          num = num * 10 + x % 10;
          x = x / 10;
      }
      if (num != (int) num) {
        return 0;
      }
      return (int) num;
  }
}
```

## Spent time

* 7분

## Review

* Stack 을 써야겠다라는 아이디어를 얻고 무식하게 코딩했다.
* 다른 풀이를 보니 깔끔하고 우아한 방법은 아니다.
* `%(Arithmetic Operators)`  방법과 내 방법 모두 O(n) 이지만, 엄밀히 내 아이디어는 O(2n) 이고, 공간 복잡도가 더 높다.

