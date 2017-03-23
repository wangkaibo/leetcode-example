# 最大子列和问题

最近在学习一些常用的经典算法，比较经典的一个问题就是给定一个序列，求连续子列的最大和。用数学语言描述如下：

给定序列

![aa](https://latex.codecogs.com/gif.latex?[A_{1},A_{2},A_{3},...,A_{n}]) 

计算出：

![aa](http://7xu5j5.com1.z0.glb.clouddn.com/max_child_sum.gif)

LeetCode 链接 [Maximum Subarray](https://leetcode.com/problems/maximum-subarray)

这个问题使用在线最优化求解(Online Optimization)算法是效率最高的,只需要维护两个变量，一次循环就可以完成。


```python

class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        max_sum =  nums[0]
        current_sum = 0
        for num in nums:
            current_sum += num
            if current_sum > max_sum:
                max_sum = current_sum
            if current_sum < 0:
                current_sum = 0; # 不可能使后面的和增大，抛弃
                
        return max_sum

```

下面是运行结果：
![LeetCode](http://7xu5j5.com1.z0.glb.clouddn.com/Maximum_Subarray.png)

可见这是执行效率比较高的解法，时间复杂度为O(n)，但是 LeetCode 还推荐去练习另一种分而治之的解决办法，应该是类似二分法。有时间再去实现下。
