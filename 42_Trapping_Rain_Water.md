## 问题描述
给定的 n 个非负整数表示每个宽度为 1 栅栏的海拔地图的高度，计算在下雨之后能够捕获多少水

举例：

给出 [0,1,0,2,1,0,1,3,2,1,2,1], 返回 6。

![示例图](http://www.leetcode.com/static/images/problemset/rainwatertrap.png)

```python
class Solution(object):
    def trap(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        max_index = height.index(max(height))

        height_len = len(height)

        current_max = 0;

        total = 0

        for i in range(max_index):
            if height[i] > current_max:
                current_max = height[i]
            else:
                total += current_max - height[i]

        current_max = height[height_len - 1];

        for i in range(max_index, height_len)[::-1]:
            if height[i] > current_max:
                current_max = height[i]
            else:
                total += current_max - height[i]
        print total

height_list = [0,1,0,2,1,0,1,3,2,1,2,1]

solution = Solution()

solution.trap(height_list)
```
