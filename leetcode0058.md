# leetcode0058



### 题目地址：

---

https://leetcode-cn.com/problems/length-of-last-word/



### 题目描述

---

```text
给定一个仅包含大小写字母和空格 ' ' 的字符串，返回其最后一个单词的长度。

如果不存在最后一个单词，请返回 0 。

说明：一个单词是指由字母组成，但不包含任何空格的字符串。

示例:

输入: "Hello World"
输出: 5
```



### 思路

---

1.先用一个变量存储去掉末尾空格的字符串

2.再用一个for循环来遍历，用一个if条件判断，当再碰到空格的时候break，否则就count++



### 代码

---

```java
class Solution {
    public int lengthOfLastWord(String s) {
        
        int count = 0;
        int i = s.length()-1;
        while(i >= 0 && s.charAt(i) == ' '){
            i--;
        }
            for(int j = i;j >= 0;j --){
                if(s.charAt(j) == ' '){
                   break;  
            }
                count ++;
    } 
        return count;
    }
}
```



### 问题与解决

---

Question：

当时在最后空格的去除的地方有点绕，不知道该怎么去掉末尾的空格。

Answer：

1.从字符串的末尾开始遍历，碰到空格就执行i--，没有碰到就break

2.用trim()方法

##### *trim()方法*

```text
trim()的作用是去掉字符串两端的多余的空格，注意，是两端的空格，且无论两端的空格有多少个都会去掉，当然
中间的那些空格不会被去掉，如：
String s = "  a s f g      ";
String s1 = s.trim();
那么s1就是"a s f g"，可见，这和上面所说的是一样的。
trim()不仅可以去掉空格，还能去掉其他一些多余的符号，这些符号分别是：
\t  \n  \v  \f  \r  \x0085  \x00a0  ?  \u2028  \u2029
翻译过来分别是：水平制表符，换行符，垂直制表符，换页符，回车，后面的这几个除了问号外，其他的都是转义符形式写法。
```

