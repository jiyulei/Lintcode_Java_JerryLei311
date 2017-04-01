## 题目：

There is an integer array which has the following features:

* The numbers in adjacent positions are different.
* A\[0\] 
  &lt;
   A\[1\] 
  &
  &
   A\[A.length - 2\] 
  &gt;
   A\[A.length - 1\].

We define a position P is a peek if:

```
A[P] 
>
 A[P-1] 
&
&
 A[P] 
>
 A[P+1]

```

Find a peak element in this array. Return the index of the peak.

##### Notice

The array may contains multiple peeks, find any of them.

**Example**

Given`[1, 2, 1, 3, 4, 5, 7, 6]`

Return index`1`\(which is number 2\) or`6`\(which is number 7\)

[**Challenge**](http://www.lintcode.com/en/problem/find-peak-element/#challenge)

Time complexity O\(logN\)

## 分析：

此题要求找到任意一个峰， 一刀切下去有四种情况 ： 上升段，下降段，谷，峰（直接返回）

若mid在上升段则mid 右侧肯定有解（因为题目说至少有一个峰所以最后一段为下降），若mid在下降段则mid左侧肯定有峰（因为一开始上升），若mid刚好在谷底则左右至少各有一个峰（因为第一段上，最后一段下降，所以至少有两个峰才会有一个谷）

## 代码：

```
class Solution {
    /**
     * @param A: An integers array.
     * @return: return any of peek positions.
     */
    public int findPeak(int[] A) {
        // write your code here
        int start = 0;
        int end = A.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (A[mid] > A[mid + 1] && A[mid] > A[mid - 1]) {
                return mid;
            } else if (A[mid] < A[mid + 1] && A[mid] > A[mid - 1]) {
                start = mid;
            } else {
                end = mid;
            }
        }
        if (A[start] > A[end]) {
            return start;
        } else {
            return end;
        }
    }
}

```



