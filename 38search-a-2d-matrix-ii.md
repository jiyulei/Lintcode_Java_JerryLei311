## 题目：

Write an efficient algorithm that searches for a value in an m x n matrix, return the occurrence of it.

This matrix has the following properties:

* Integers in each row are sorted from left to right.
* Integers in each column are sorted from up to bottom.
* No duplicate integers in each row or column.

**Example**

Consider the following matrix:

```
[
  [1, 3, 5, 7],
  [2, 4, 7, 8],
  [3, 5, 9, 10]
]

```

Given target =`3`, return`2`.

## 分析：

#### 此题要求时间复杂度为O\(M+N），矩阵中任意一个元素都比他下面的和右面的小 ，根据这个规律分析一下得到任意一个位置的情况如下：![](/assets/FullSizeRender 2.jpg)

这种情况下如果从左下角出发，target比他大就往右移一个比较，如果比他小就往上走一行，如果相等则记数一次，并且挪动到N位置（即往右上走一个）

#### 总结：

#### 这种题型起始的判断位置肯定不会在任意一个地方，所以分析左右上下四个角发现，t和左下角的元素比较后可以确定往哪个方向走。

#### 代码：

`public class Solution {`

`    /**`

`     * @param matrix: A list of lists of integers`

`     * @param: A number you want to search in the matrix`

`     * @return: An integer indicate the occurrence of target in the given matrix`

`     */`

`    public int searchMatrix(int[][] matrix, int target) {`

`        // write your code here`

`        if (matrix.length == 0 || matrix == null) {`

`            return 0;`

`        }`

`        if (matrix[0].length == 0 || matrix[0] == null) {`

`            return 0;`

`        }`

`        int m = matrix.length; `

`        int n = matrix[0].length;`

`        int row = m - 1;`

`        int col = 0;`

`        int count = 0;`

`        while ((row >= 0) && (col < n)) {`

`            if (matrix[row][col] < target) {`

`                col++;`

`            } else if (matrix[row][col] > target) {`

`                row--;`

`            } else {`

`                count++;`

`                row--;`

`                col++;`

`            }`

`        }`

`        return count;`

`    }`

`}`





