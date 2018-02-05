## 问题分析：
#### 删除给定元素
本题要求在本数组中进行元素修改,因此要用变量标记数组修改位置,最终用新修改过的数组覆盖原数组。
## 编程实现
```C++
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int i=0,j=0;
        if(nums.empty()) return j;
        for(i=0;i<nums.size();i ++)
        {
            if(nums[i]!=val)
                nums[j++]=nums[i];
        }
        return j;
        
    }
};
```
## 总结体会
1. 相当于数组中元素的替换
2. 在同一数组内操作不能重新开辟一个数组
