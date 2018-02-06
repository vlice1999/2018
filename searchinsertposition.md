## 问题分析：
#### 搜索插入位置
如果在数组内能找到该数字就输出对应的位置,未能找到就按序插入然后输出位置
## 编程实现：
```C++
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int i=0,j=0;
        for(i=0;i<nums.size();i ++)
        {
            if(nums[i]==target)
                return i;
        }
        for(j=0;j<nums.size();j ++)
        {
            if(nums[j]>=target)
                return j;
        }
        if(j==nums.size())
            return j;
    }
};
```
## 总结体会：
分类讨论+循环;需要考虑的就是能找到和不能找到的两种情况。
