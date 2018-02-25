# 3Sum
## 问题分析：
求三个数之和等于0,先进行排序再遍历
## 编程实现：
```C++
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> res;
        sort(nums.begin(), nums.end());
        int k=0;
        for(k=0;k<nums.size();++k)
        {
            if(nums[k]>0) break;
            if(k>0&&nums[k]==nums[k-1]) continue;
            int target=0-nums[k];
            int i=k+1;
            int j=nums.size()-1;
            while(i<j)
            {
                if(nums[i]+nums[j]==target)
                {
                    res.push_back({nums[k],nums[i],nums[j]});
                    while(i<j&&nums[i]==nums[i+1]) ++i;
                    while(i<j&&nums[j]==nums[j-1]) --j;
                    ++i; 
                    --j;
                } 
                else if(nums[i]+nums[j]<target)  ++i;
                else --j;
            }
        }
        return res;
    }
};
```

# 4Sum
## 问题分析：
最接近给定值的三个数之和,用遍历数组加上结合指针
## 编程实现：
```C++
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        int closest=nums[0]+nums[1]+nums[2];
        int diff=abs(closest-target);
        sort(nums.begin(), nums.end());
        int i=0;
        for(i=0;i<nums.size()-2;++i)
        {
            int left=i+1; 
            int right=nums.size()-1;
            while(left<right)
            {
                int sum=nums[i]+nums[left]+nums[right];
                int newDiff=abs(sum-target);
                if(diff>newDiff)
                {
                    diff=newDiff;
                    closest=sum;
                }
                if(sum<target)  ++left;
                else --right;
            }
        }
        return closest;
    }
};
```
