## 题目：

Given a mountain sequence of`n`integers which increase firstly and then decrease, find the mountain top.

**Example**

Given`nums`=`[1, 2, 4, 8, 6, 3]`return`8`  
Given`nums`=`[10, 9, 8, 7]`, return`10`

## 分析：

先升后降 判断一刀切下去mid 在上升段还是下降段 上升target在右边 否则在左边



## 代码：

```
public class Solution {
    /**
     * @param nums a mountain sequence which increase firstly and then decrease
     * @return then mountain top
     */
    public int mountainSequence(int[] nums) {
        // Write your code here
        if (nums == null || nums.length == 0) {
            return -1;
        }
        int start = 0;
        int end = nums.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] < nums[mid + 1]) {
                start = mid;
            } else {
                end = mid;
            }
        }
        if (nums[start] > nums[end]) {
            return nums[start];
        } else {
            return nums[end];
        }
    }
}
```

##  



