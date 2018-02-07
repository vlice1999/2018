## 问题分析：
#### 求最大子数组之和
每一步维护两个变量,全局最优和局部最优
## 编程实现：
```C++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        if(nums.size()==0) return 0;
        int x=INT_MIN,y=0;
        for(int num : nums)
        {
            y=max(y+num,num);
            x=max(x,y);
        }
        return x;
    }
};
```
## 总结体会：
是数组中求最大值的子数组所以数字排列顺序不变,遍历每一个数字然后将这个数字与之前数字的和+这个数字比较大小来决定哪一个大来存入最终的数组中
