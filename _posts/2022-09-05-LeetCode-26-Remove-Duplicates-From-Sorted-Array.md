---
title: LeetCode 26. Remove Duplicates From Sorted Array
date: 2022-09-05 23:50:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Remove Duplicates From Sorted Array
comments: true
---

## [26. Remove Duplicates From Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

## Problem

```
Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array nums. More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result. It does not matter what you leave beyond the first k elements.

Return k after placing the final result in the first k slots of nums.

Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.

Custom Judge:

The judge will test your solution with the following code:

int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
If all assertions pass, then your solution will be accepted.
```

## Questions before reading example

// can i only use O(1) extra memory?
// is it possible to receive an empty input ?
// is it possible to receive an array contains negative value?

## Example

```
Example 1:

Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
Example 2:

Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).


```

## Solution

* 나의 풀이

```java
class Solution {
  public int removeDuplicates(int[] nums) {
    int currentNum = -1000;
    int count = 0;
    for (int i = 0; i < nums.length; i++) {
      if (currentNum == nums[i]) {
        nums[i] = 99999;
        continue;
      }
      currentNum = nums[i];
      count++;
    }

    Arrays.sort(nums);

    return count;
  }
}
```
* 다른 깔끔 & 좋은 아이디어 풀이
```java
public class Solution {
  public int removeDuplicates(int[] nums) {
    int i = 0;
    for (int n : nums)
      if (i == 0 || n > nums[i-1])
        nums[i++] = n;
    return i;
  }
}
```

## Spent time
* 10분?


## Review
* 처음에 영어 내용만 읽고 문제를 이해하기가 어려웠다.
* array 의 index 를 수정할 생각에.. 머리가 하앴지만,필살기?급인 Arrays.sort() 를 이용하여서 풀었다.
* 매직넘버가 두개나 있는 좋은 코드는 아니어서, 디스커션을 찾아보았는데, 역시나 깔끔하고 좋은 방법이..
* 별거 아닌 코드처럼 보이지만, 저런 방법을 어떻게 한번에 생각해내서 풀 수 있을까.. 그저 감탄이다.
