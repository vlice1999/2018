## 问题分析：
#### 从有序数组中去除重复项
利用下标访问数组中的值
## 编程实现：
```C++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int i=0,j=0;
        int n=nums.size();
        if(nums.empty()) return 0;
        for(i=0;i<n;++ i)
        {
            if(nums[i]!=nums[j])
                nums[++ j]=nums[i];
        }
    }
};
```
## 总结体会：
1. 指针：一个快指针一个慢指针
2. return j+1:因为j从零开始,所以计算个数时需要+1
