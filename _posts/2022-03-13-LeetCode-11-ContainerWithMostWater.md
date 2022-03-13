---
title: LeetCode 78. Subsets date: 2022-03-13 19:30:00 +0900
categories: [leetcode, algorithm]
tags: [algorithm]
description : Container With Most Water
comments: true
---

## [11. Container With Most Water](https://leetcode.com/problems/container-with-most-water/)

## Problem

```
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.



```

## Questions before reading example

## Example

```
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.


Input: height = [1,1]
Output: 1

```

## Solution

* 나의 풀이 (1차 시도 - 실패)

```java
class Solution {

  public int maxArea(int[] height) {
    // 무식하게 풀어보았지만 실패 ..
    int maxArea = 0;
    for (int i = 1; i < height.length + 1; i++) {
      for (int j = i; j > 0 && i < height.length; j--) {
        int areaWidth = j;
        int areaHeight = Math.min(height[i], height[i - j]);
        int area = areaWidth * areaHeight;
        if (area > maxArea) {
          maxArea = area;
        }
      }
    }
    return maxArea;

  }
}
```

* 나의 풀이 (2차 시도 - 성공)

```java

class Solution {

  public int maxArea(int[] height) {
    // Discussion 에서 힌트를 얻은 후
    int left = 0;
    int right = height.length - 1;
    int maxArea = 0;
    while (left < right) {
      maxArea = Math.max(maxArea, (Math.min(height[left], height[right]) * (right - left)));
      if (height[left] < height[right]) {
        left++;
      } else {
        right--;
      }
    }

    return maxArea;

  }
}
```

## Spent time

* 30분

## Review

* 분명 풀어 본 익숙한 문제이다.. 과거 NHN 신입 코테 수준을 검토할때 풀어 본 문제다.
* 처음 접근은.. 시간복잡도를 고려하지 않고, 규칙을 찾아 for 문에 때려박는다고 생각하고 무식하게 풀어보려고 했다.
  * ex)
    * 1 8 일때 => 1 * 1
    * 1 8 6 일때 => 1 * 2, 6 * 1
    * 1 8 6 2 일때 => 1 * 3, 2 *2, 2 * 1
* 예제의 답은 모두 풀었으나 시간복잡도 O(n^2) 으로 인해 timeout..
* 시간 복잡도를 개선하려 고민해보았다.
  * memoization 을 활용할 수 있는 DP 문제 인가? NO
  * Map 활용해서 for 문을 줄일 수 있는가? NO
* 결국 디스커션을 보았고.. 문제 접근을 달리하여 아주 심플하게 풀 수 있었다.
  * left 와 right 를 활용하는..
* 처음부터 무지성으로 문제를 접근해서 실패했다..
* 아마 계속 시도해도 전혀 생각하지 못했을 것이다. 생각해내더라도 왠지 코너케이스가 있을 것 같아 불안했을 것이다.
* 문제를 올바르게 파악하고 해결하려는 아이디어를 떠올리는게 정말 중요하다..
