# 空格替换

请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

示例 1：

输入：s = "We are happy."
输出："We%20are%20happy."

限制：0 <= s 的长度 <= 10000
链接：https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof

## 解决方案一

使用开辟一个新数组，然后逐个判断数组元素，用append方法逐个替换。注意字符串和字符数组的区别和转换函数。

```java
public String replaceSpace(String s) {
    char[] b = s.toCharArray(); //先定义一个字符数组，把传入的字符串s用toCharArray()方法改成字符数组，否则用不了下标来定位
    StringBuilder stringBuilder =new StringBuilder(); //开一个新的数组，stringbuilder可以使用append功能，少占用内存
    for (int i=0;i<s.length();i++){
        if (b[i] == ' '){
            stringBuilder.append("%20");
        }
        else
            stringBuilder.append(b[i]);
    }
    return stringBuilder.toString(); //返回时注意重新改回字符串类型

}
```

## 解决方案二

Java官方造好了轮子我们就用嘛，使用replaceAll方法，前面填要判断的字符，后面写替换的文本。但不知道面试时能不能用。

```java
public String replaceSpace2(String s){
    return s.replaceAll(" ","%20"); //调用库函数写最简洁的方法，前面填要判断的字符，后面写替换的文本
}
```