# leetcode0067



### 题目地址：

------

https://leetcode-cn.com/problems/add-binary/



### 题目描述

------

```text
给定两个二进制字符串，返回他们的和（用二进制表示）。

输入为非空字符串且只包含数字 1 和 0。

示例 1:

输入: a = "11", b = "1"
输出: "100"

示例 2:

输入: a = "1010", b = "1011"
输出: "10101"
```



### 思路

------

整体思路是将两个字符串较短的用 000 补齐，使得两个字符串长度一致，然后从末尾进行遍历计算，得到最终结果。
本题解中大致思路与上述一致，但由于字符串操作原因，不确定最后的结果是否会多出一位进位，所以会有 2 种处理方式：

第一种，在进行计算时直接拼接字符串，会得到一个反向字符，需要最后再进行翻转
第二种，按照位置给结果字符赋值，最后如果有进位，则在前方进行字符串拼接添加进位

时间复杂度：O(n)

### 代码

------

```java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int lena = a.length();
        int lenb = b.length();
        int temp = 0;
            for(int i = lena - 1,j = lenb -1;i >= 0 || j >= 0;i--,j-- ){
                int sum = temp;
                sum += i >= 0 ? a.charAt(i) - '0' : 0;
                sum += j >= 0 ? b.charAt(j) - '0' : 0;
                sb.append(sum % 2);
                temp = sum / 2;
        }
        sb.append(temp == 1 ? temp : "");
            return sb.reverse().toString();
    }
}
```



### 问题与解决

------

Question：

没怎么懂还需多看几遍。

Answer：

。



