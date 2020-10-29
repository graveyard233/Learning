# 二维数组中的查找

在一个 n * m 的二维数组中，每一行都按照**从左到右递增**的顺序排序，每一列都按照从**上到下递增**的顺序排序。
请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
链接：https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof

## 解决方案

由于给定的二维数组具备每行从左到右递增以及每列从上到下递增的特点，当访问到一个元素时，可以排除数组中的部分元素。

从二维数组的左下角开始遍历，假如这个数比目标数大，则去上面一行，假如这个数小于目标数，去右边一列。

这种方法不会错过任何一个元素。

```java
public boolean findNumberIn2DArray(int[][] matrix, int target) {
    if (matrix.length == 0) //先判断矩阵是否为空
        return false;
    int rows = matrix.length;  //获取行
    int cols = matrix[0].length; //获取列
    int row = rows - 1, col = 0;
    while (row >= 0 && col < cols) { //从矩阵的左下角开始遍历
        if (matrix[row][col] > target) //假如这个数比目标数大，则去上面一行
            row--;
        else if (matrix[row][col] < target) //假如这个数小于目标数，去右边一列
            col++;
        else
            return true;
    }
    return false;
}
```