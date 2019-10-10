
## [164] 最大间距(Maximum Gap)

- 类型：排序类

- 难度: 困难

#### 题目描述:

给定一个无序的数组，找出数组在排序之后，相邻元素之间最大的差值。

如果数组元素个数小于 2，则返回 0。

#### 示例:

输入: [3,6,9,1]

输出: 3

解释: 排序后的数组是 [1,3,6,9], 其中相邻元素 (3,6) 和 (6,9) 之间都存在最大差值 3。


#### 思路

这道题本质上还是排序,将冒泡排序做了修改:
1.冒泡排序,每次求得最大值时,与上一个最大值相减取得差值
2.依次求取差值,并与上次求取的差值进行比较,大则替换

#### 代码

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var maximumGap = function (nums) {
  let res = 0
  for (let i = nums.length; i >= 0; i--) {
    for (let j = 0; j < i; j++) {
      if (nums[j] > nums[i]) {
        [nums[j], nums[i]] = [nums[i], nums[j]]
      }
    }
    if (i !== nums.length && res < nums[i + 1] - nums[i]) {
      res = nums[i + 1] - nums[i]
    }
  }
  return res
};
```

#### 结果

Accepted
- 18/18 cases passed (308 ms)
- Your runtime beats 16.51 % of javascript submissions
- Your memory usage beats 53.05 % of javascript submissions (35.3 MB)

#### 复杂度分析：

- 时间复杂度：O(n^2)，

- 空间复杂度：O(1)。

