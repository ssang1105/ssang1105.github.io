---
title: LeetCode 20. Valid Parentheses
date: 2022-09-05 22:30:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Valid Parentheses
comments: true
---

## [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

## Problem

```
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
```

## Questions before reading example

// * Can I get an empty value in the input?
// * Can i get any other inputs except brackets?
// * Can i use Stack library?

## Example

```
Example 1:

Input: s = "()"
Output: true
Example 2:

Input: s = "()[]{}"
Output: true
Example 3:

Input: s = "(]"
Output: false


```

## Solution

* 나의 풀이

```java
class Solution {
  public boolean isValid(String s) {
    if (s.length() < 1) {
      return false;
    }
    Deque<Character> stack = new ArrayDeque<>();
    for (char character : s.toCharArray()) {
      if (character == '(' || character == '{' || character == '[') {
        stack.push(character);
      }
      else if (character == ')') {
        if (stack.isEmpty()) {
          return false;
        }
        char charInStack = stack.pop();
        if (charInStack != '(') {
          return false;
        }
      } else if (character == '}') {
        if (stack.isEmpty()) {
          return false;
        }
        char charInStack = stack.pop();
        if (charInStack != '{') {
          return false;
        }
      } else if (character == ']') {
        if (stack.isEmpty()) {
          return false;
        }
        char charInStack = stack.pop();
        if (charInStack != '[') {
          return false;
        }
      }
    }

    return stack.isEmpty();
  }
}
```
* 다른 깔끔 풀이
```java
public class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<Character>();
        // Iterate through string until empty
        for(int i = 0; i<s.length(); i++) {
            // Push any open parentheses onto stack
            if(s.charAt(i) == '(' || s.charAt(i) == '[' || s.charAt(i) == '{')
                stack.push(s.charAt(i));
            // Check stack for corresponding closing parentheses, false if not valid
            else if(s.charAt(i) == ')' && !stack.empty() && stack.peek() == '(')
                stack.pop();
            else if(s.charAt(i) == ']' && !stack.empty() && stack.peek() == '[')
                stack.pop();
            else if(s.charAt(i) == '}' && !stack.empty() && stack.peek() == '{')
                stack.pop();
            else
                return false;
        }
        // return true if no open parentheses left in stack
        return stack.empty();
    }
}
```

## Spent time



## Review
* 처음에 스택을 사용해서 푼다는 것만 기억이 나고.. 구체적으로 어떻게 풀어야할지 기억이 잘 나지 않았다.
  * 대학생때부터 수없이 풀었던 문제인데..
* 한번에 풀지 못하고, 코너 케이스 (Ex. 입력이 "]" 인 경우) 를 해결해나가며 3번만에 풀었다.
