---
title: LeetCode之数据结构——数组demo3
date: 2019-4-9 21:32:50
tags: [data structure,LeetCode,array]
categories: [数据结构,LeetCode]
---
![data-structure-array-plusone](data-structure-array-plusone/adorable-bench-blurred-background-1767434.jpg) 

**代码维护于GitHub：[https://github.com/zrxJuly/data-structure](https://github.com/zrxJuly/data-structure)**
> ***Coding Question:***
> Given a non-empty array of digits representing a non-negative integer, plus one to the integer.
> The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.
> You may assume the integer does not contain any leading zero, except the number 0 itself.
>
> ***编程题:***
> 给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加1.
> 最高位存放于数组首位，并且数组中的每个元素只包含一个数字.
> 你可以假设该整数除了整数0之外，不会以0开头.
> 

例如：
```
输入：[1,2,3]
输出：[1,2,4]
解释：输入数组表示数字123.
```

<!-- more -->

代码：
```java
public class PlusOne {
    /**
     * |-思路分析：逢十进一
     *      从最后一位数组开始向前遍历int数组，
     *      若最后一位数为9，则将该数值赋为0(逢十进一)，然后依次向前同理，
     *      若前一位也为9，则赋为0，再向前遍历，若目标数不为9，则该数值+1.
     *      若数组首位数为0，则需要在数组首位前添加一个数1.
     * @param digits
     * @return
     */
    public static int[] plusOne(int[] digits) {
        // 从数组最后一位数（digits.length-1）开始判断，若<9，直接+1，若=9，采用逢十进一方法.
        int dIndex = digits.length-1;
        boolean isContinue = true;

        while (isContinue && dIndex >= 0) {
            if (digits[dIndex] < 9) {
                digits[dIndex] += 1;
                isContinue = false;
            } else {
                digits[dIndex] = 0;
            }
            dIndex --;
        }

        // while循环转化后若首位为0，则在原数组首位前需加一位1.
        if (digits[0] == 0) {
            int[] newDigits = new int[digits.length+1];
            newDigits[0] = 1;
            for (int i = 1; i < digits.length; i ++) {
                newDigits[i] = digits[i-1];
            }
            return newDigits;
        }

        return digits;
    }

    /**
     * |-More Simple Solution:
     *
     */
    public static int[] plusOneSimple (int[] digits) {
        int dIndex = digits.length-1;
        for (int i = dIndex; i >= 0; i --) {
            if (digits[i] < 9) {
                digits[i] += 1;
                return digits;
            }
            // if ==9
            digits[i] = 0;
        }
        // 显然，上面for循环遍历完成后若走到该方法，说明数组首位为逢十进一数.
        int[] newDigits = new int[digits.length+1];
        newDigits[0] = 1;

        return newDigits;
    }

    public static void main(String[] args) {
        int[] digits = {9,8,9,9};
//        int[] result = plusOne(digits);
//        System.out.print("result is:");
//        for (int i = 0; i < result.length; i ++) {
//            System.out.print(result[i] + ",");
//        }

        int[] result2 = plusOneSimple(digits);
        System.out.print("result2 is:");
        for (int i = 0; i < result2.length; i ++) {
            System.out.print(result2[i] + ",");
        }
    }
}
```

