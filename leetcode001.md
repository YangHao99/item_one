# leetcode001

题目地址：
---
https://leetcode-cn.com/problems/two-sum/



题目描述
---
```text
	给定一个整数数组 nums 和一个目标target,请你在该数组中找出和为目标值的那两个整数，并返回他们的数组下标。你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

示例:
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```



思路
---
1. 利用双层for循环遍历数组，如果找到两个数字之和为目标值，即返回对应下标
2. 利用hashMap两次遍历数组，第一次遍历将数组装入hashmap，第二次逐个比对数组中是否有一个值等于目标值减去i



代码
---
```java-for
	class Solution {
    public int[] twoSum(int[] nums, int target) {
        for(int i=0;i<nums.length-1;i++){
            for(int j=i+1;j<=nums.length-1;j++){               
                if(nums[i]+nums[j]==target){	
                    return new int[]{i,j};
                }
            }
        }
        //抛出异常
        throw new IllegalArgumentException("No two sum solution");
    }
}
```



```java-hashmap
	class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {  
            map.put(nums[i], i);
        }
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            
            //判断是否在这个值是否在数组当中并且不是它本身
            if (map.containsKey(complement) && map.get(complement) != i) {
                return new int[] { i, map.get(complement) };
            }
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}

```




问题与解决
---
method1：
Q1：error: missing return statement  缺少返回值
S1：没有覆盖所有可能的路径 当没有找到sum==target时返回的值

method2:
map常用方法：
- containsKey(Object key)    如果此映射包含指定键的映射关系，则返回 true。
- get(Object key)   返回指定键所映射的值；如果对于该键来说，此映射不包含任何映射关系，则返回 null。
-  put(K key, V value)   在此映射中关联指定值与指定键。
- isEmpty()   如果此映射未包含键-值映射关系，则返回 true。



