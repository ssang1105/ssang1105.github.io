---
title: LeetCode 206. ReverseLinkedList
date: 2022-02-07 23:30:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : FizzBuzz
comments: true
---

## [206. ReverseLinkedList](https://leetcode.com/problems/reverse-linked-list/)

## Problem

```
Given the head of a singly linked list, reverse the list, and return the reversed list.

```

## Questions before reading example


## Example

```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]

Input: head = [1,2]
Output: [2,1]

Input: head = []
Output: []
```

## Solution
* 나의 풀이
```java
class Solution {
  public ListNode reverseList(ListNode head) {
    if (head == null) {
      return null;
    }

    Stack<ListNode> stack = new Stack<>();
    stack.push(head);
    while (head.next != null) {
      head = head.next;
      stack.push(head);
    }

    ListNode result = stack.pop();
    ListNode tmp = result;
    while (!stack.isEmpty()) {
      tmp.next = stack.pop();
      tmp = tmp.next;
    }
    tmp.next = null;

    return result;
  }
}
```
* 다른 사람 풀이 (2개)

```java
public ListNode reverseList(ListNode head) {
    /* iterative solution */
    ListNode newHead = null;
    while (head != null) {
        ListNode next = head.next;
        head.next = newHead;
        newHead = head;
        head = next;
    }
    return newHead;
}

public ListNode reverseList(ListNode head) {
    /* recursive solution */
    return reverseListInt(head, null);
}

private ListNode reverseListInt(ListNode head, ListNode newHead) {
    if (head == null)
        return newHead;
    ListNode next = head.next;
    head.next = newHead;
    return reverseListInt(next, head);
}
```

## Spent time
* 30분

## Review

* 문제를 보자마자 Stack 을 생각했다.
* 처음에는 Stack 에 ListNode 가 아니라 Integer 를 담는 실수를 했다. 도저히 뒤집을 수 있는 코드가 떠오르지 않았다.
* Stack 에 ListNode 를 담고, while 문 안에서 pop 하면서 뒤집을때에도 생각보다 어려웠다.
* Node 가 나오는 문제는 나중에 다시 보자.

