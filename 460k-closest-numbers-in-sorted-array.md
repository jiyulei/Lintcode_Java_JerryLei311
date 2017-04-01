## 题目：

Given a target number, a non-negative integer`k`and an integer array A sorted in ascending order, find the k closest numbers to target in A, sorted in ascending order by the difference between the number and target. Otherwise, sorted in ascending order by number if the difference is same.

**Example**

Given A =`[1, 2, 3]`, target =`2`and k =`3`, return`[2, 1, 3]`.

Given A =`[1, 4, 6, 8]`, target =`3`and k =`3`, return`[4, 1, 6]`.



Requirement : O\(logn + k\) time complexity.

## 分析：

此题需要用二分先找到target的index ，然后用双指针将target两边的元素按距离target由小至大排列。

## 代码：

```
public class Solution {
    /**
     * @param A an integer array
     * @param target an integer
     * @param k a non-negative integer
     * @return an integer array
     */
    public int[] kClosestNumbers(int[] A, int target, int k) {
        // Write your code here
        if (A == null || A.length == 0) {
            return A;
        }
        if (k > A.length) {
            return A;
        }
        int[] results = new int[k];
        int index = firstIndex(A, target);
        int start = index - 1;
        int end = index;
        for (int i = 0; i < k; i++) {
            if (start < 0) {
                results[i] = A[end++];
            } else if (end >= A.length) {
                results[i] = A[start--];
            } else {
                if (target - A[start] > A[end] - target) {
                    results[i] = A[end++];
                } else {
                    results[i] = A[start--];
                }
            }
        }
        return results;
    }
    private int firstIndex(int[] A, int target) {
        int start = 0;
        int end = A.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (A[mid] == target) {
                 end = mid;
            } else if (A[mid] < target) {
                start = mid;
            } else {
                end = mid;
            }
        }
        if (A[start] == target) {
            return start;
        }
        if (A[end] >= target) { // if target< end && target != start means [start,t,end]
            return end;
        }
        return A.length;
    }
}


```



  






