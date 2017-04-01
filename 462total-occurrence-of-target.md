## 题目：

Given a target number and an integer array sorted in ascending order. Find the total number of occurrences of target in the array.

**Example**

Given`[1, 3, 3, 4, 5]`and target =`3`, return`2`.

Given`[2, 2, 3, 4, 6]`and target =`4`, return`1`.

Given`[1, 2, 3, 4, 5]`and target =`6`, return`0`.

## 分析：

我的解法： 先利用二分法找到任意一个target的位置， 然后从该位置往两边走（双指针）记录出现了几次。直到两边都碰到不等的值返回记录次数。

### 代码：

```
public class Solution {
    /**
     * @param A an integer array sorted in ascending order
     * @param target an integer
     * @return an integer
     */
    public int totalOccurrence(int[] A, int target) {
        // Write your code here
        if (A == null || A.length == 0) {
            return 0;
        }
        int start = 0;
        int end = A.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (A[mid] < target) {
                start = mid;
            } else if (A[mid] > target) {
                end = mid;
            } else {
                return countOccur(A,mid,target);
            }
        }
        if (A[start] == target) {
            return countOccur(A,start,target);
        } else if (A[end] == target) {
            return countOccur(A,end,target);
        } else {
            return 0;
        }
    }
    private int countOccur(int[] A, int targetIndex,int target) {
        int count = 0;
        for (int i = targetIndex; i < A.length; i++) {
            if (A[i] == target) {
                count++;
            } else {
                break;
            }
        }
        for (int j = targetIndex; j > 0; j--) {
            if (A[j - 1] == target) {
                count++;
            } else {
                break;
            }
        }
        return count;
    }
}
```



