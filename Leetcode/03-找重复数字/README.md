# 找出数组中的重复数字

在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

示例 1：
输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof

## 解决方案一

开辅助数组，别人称之为记忆存储法

```java
public int findRepeatNumber(int[] nums) {
    int b = nums.length;
    int[] a = new int[b];//动态开辟一个辅助数组，
    for (int i = 0; b > i; i++) {
        a[nums[i]]++;//下标放对应数字出现的次数，出现一次就+一次
        if (a[nums[i]] >= 2)
            return nums[i];//一旦大于2就直接返回，结束运行
    }
    return -1;//没重复数值
```

## 解决方案二

**原地置换**

我们还可以不使用临时数组，我们在遍历的时候把数组nums中的值放到对应的位置上，比如某个元素是5，我们就把他放到nums[5]中，每次放入的时候查看一下这个位置是否放入了正确的值，如果已经放入了正确的值，就说明重复了，我们直接返回即可。

```java
public int YuanDiZhiHuan(int[] nums) {
    for (int i = 0; i < nums.length; i++) {
        //位置正确，先不用管
        if (i == nums[i])
            continue;
        //出现了重复，直接返回
        if (nums[i] == nums[nums[i]]) {
            return nums[i];
        }
        //交换
        int temp = nums[nums[i]];
        nums[nums[i]] = nums[i];
        nums[i] = temp;
        //这里的i--是为了抵消掉上面的i++，
        //交换之后需要原地再比较
        i--;
    }
    return -1;

}
```