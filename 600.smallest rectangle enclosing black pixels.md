## 题目：

An image is represented by a binary matrix with 0 as a white pixel and 1 as a black pixel. The black pixels are connected, i.e., there is only one black region. Pixels are connected horizontally and vertically. Given the location \(x, y\) of one of the black pixels, return the area of the smallest \(axis-aligned\) rectangle that encloses all black pixels.

**Example**

For example, given the following image:

\[

 "0010",

 "0110",

 "0100"

\]

and x = 0, y = 2,  
 Return 6.

#### 解法：



此题关键在于找到上下左右四个边界 利用二分法找到四个边界即可算面积

  


`public class Solution {`

` /**`

` * @param image a binary matrix with '0' and '1'`

` * @param x, y the location of one of the black pixels`

` * @return an integer`

` */`

` public int minArea(char[][] image, int x, int y) {`

` // Write your code here`

` if (image == null || image.length == 0 || image[0].length == 0) {`

` return 0;`

` }`

` int left = findLeft(image,0,y);`

` int right = findRight(image,y,image[0].length - 1);`

` int top = findTop(image,0,x);`

` int down = findDown(image,x,image.length - 1);`

` return (right - left + 1) * (down - top + 1);//注意+1`

` } `

` private int findLeft(char[][] image, int start , int end) {`

` while (start + 1 < end) {`

` int mid = start + (end - start) / 2;`

` if (isEmptyColumn(image,mid)) {`

` start = mid;`

` } else {`

` end = mid;`

` }`

` }`

` if (isEmptyColumn(image, start)) {`

` return end;`

` } else {`

` return start;`

` }`

` }`

` private int findRight(char[][] image, int start, int end) {`

` while (start + 1 < end) {`

` int mid = start + (end - start) / 2;`

` if (isEmptyColumn(image,mid)) {`

` end = mid;`

` } else {`

` start = mid;`

` }`

` }`

` if (isEmptyColumn(image,end)) {`

` return start;`

` } else {`

` return end;`

` }`

` }`

` private int findTop(char[][] image, int start, int end) {`

` while (start + 1 < end) {`

` int mid = start + (end - start) / 2;`

` if (isEmptyRow(image,mid)) {`

` start = mid;`

` } else {`

` end = mid;`

` }`

` }`

` if (isEmptyRow(image,start)) {`

` return end;`

` } else {`

` return start;`

` }`

` }`

` private int findDown(char[][] image, int start, int end) {`

` while (start + 1 < end) {`

` int mid = start + (end - start) / 2;`

` if (isEmptyRow(image,mid)) {`

` end = mid;`

` } else {`

` start = mid;`

` }`

` }`

` if (isEmptyRow(image,end)) {`

` return start;`

` } else {`

` return end;`

` }`

` }`

` private boolean isEmptyColumn(char[][] image, int column) {`

` for (int i = 0; i < image.length; i++) {`

` if (image[i][column] != '0') { //元素为字符`

` return false;`

` }`

` }`

` return true;`

` }`

` private boolean isEmptyRow(char[][] image, int row) {`

` for (int i = 0; i < image[0].length; i++) {`

` if (image[row][i] != '0') {//元素为字符`

` return false;`

` }`

` }`

` return true;`

` }`

`}`

