---
title: LeetCode之数据结构——数组demo2
date: 2018-09-01 09:10:22
tags: [data structure,LeetCode,array]
categories: [数据结构,LeetCode]
---
![data structure picture](data-structure-array-LargestNumber/1.jpg) 
> ***Coding Question:***
In a given integer array nums, there is always exactly one largest element.
Find whether the largest element in the array is at least twice as much as every other number in the array.
If it is, return the index of the largest element, otherwise return -1.
***编程题：***
给定一个数组，总是存在一个最大元素。查找数组中的最大元素，该元素是否至少是数组中其他每个元素的两倍。如果是，返回最大元素的索引，否则返回-1。
***思路：***
- 首先，将给定数组中最大的元素查询出来
- 然后，遍历数组中的元素，比较数组中最大元素是否大于或等于除最大元素的其他每个元素的两倍 

<!-- more -->
下面看代码：
```java
package com.zrxjuly.ds.arrayandstring.demo;

/**
 * @author zrxJuly
 */
public class LargestNumber {
    public static void main(String[] args) {
        int nums[] = {0,0,1,1};
        int result = largestNum(nums);
        System.out.println("The result number is:" + result);
    }
    
    public static int largestNum(int[] nums) {
        // 假定数组中最大的数为数组的第一个数.
        int maxNum = nums[0];
        // 第一个数的下标值.
        int maxNumIndex = 0;
        // 先找出数组中最大的数.
        for (int m = 0; m < nums.length; m ++) {
            for (int n = m; n < nums.length; n ++) {
                if (nums[n] > maxNum) {
                    maxNum = nums[n];
                    maxNumIndex = n;
                }
            }
        }
        // 输出查看遍历后的最大数与最大数的下标.
        System.out.println("maxNum:"+maxNum);
        System.out.println("maxIndex:"+maxNumIndex);
        
        // 遍历数组，判断数组内某个元素值*2是否小于或等于maxNum，是：返回maxIndex，否：返回-1
        for (int i = 0; i < nums.length; i ++) {
            if (i == maxNumIndex) continue;
            if (nums[i] * 2 > maxNum) {
                return -1;
            }
        }
        
        return maxNumIndex;
    }
}
```