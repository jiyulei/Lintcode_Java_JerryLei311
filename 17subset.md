### 题目：

### Given a set of distinct integers, return all possible subsets.

##### Notice

* Elements in a subset must be in
  _non-descending_
  order.
* The solution set must not contain duplicate subsets.

Have you met this question in a real interview?

Yes

**Example**

If S =`[1,2,3]`, a solution is:

```
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]

```

###  分析:

此题给的数组内部是没有重复元素的。

DFS要理解递归层数的概念

（此题中每一层指的是一个subset中有相同个元素，例如【1，2】【1，3】就在同一层，而【1】就比【1，2】高一层）

【1】第一层，

【1，2】往深层走，

【1，2，3】 到底层了，此时需要返回到上一层（上一层有两个元素，所以要去掉最后这个元素）

  \*\*此时的实际过程为 【1，2，3】 ---》【1，2】

   ---》

【1，3】这是同层的一次操作

【2】

【2，3】

【3】

代码：

```
class Solution {
    /**
     * @param S: A set of numbers.
     * @return: A list of lists. All valid subsets.
     */
    public ArrayList<ArrayList<Integer>> subsets(int[] nums) {
        // write your code here
        ArrayList<ArrayList<Integer>> results = new ArrayList<>();
        ArrayList<Integer> subset = new ArrayList<>();
        if (nums == null) {
            return results;
        }
        if (nums.length == 0) {
            results.add(new ArrayList<Integer>());
            return results;
        }
        Arrays.sort(nums);
        helper(results, subset, 0, nums);
        return results;
    }
    public void helper(ArrayList<ArrayList<Integer>> results,
                       ArrayList<Integer> subset,
                       int startIndex,
                       int[] nums) {
        results.add(new ArrayList<>(subset));
        for (int i = startIndex; i < nums.length; i++) {
            subset.add(nums[i]);
            helper(results, subset,i + 1, nums);
            subset.remove(subset.size() - 1);
        }
    }
}
```

注意for循环里最后一行 removed掉最后一个元素 然后 添加i++的元素 其实是同层的操作，就是说没有改变此层元素的个数，如【1，2】--》【1，3】走过了一次循环但元素个数没变， 而递归调用就是为了往深层走，subset的元素个数加一



