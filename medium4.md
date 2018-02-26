# 4Sum
## 问题分析：
四个数之和位0,可以利用set来避免重复项的存在
## 编程实现：
```C++
class Solution {
public:
    vector<vector<int> > fourSum(vector<int> &nums, int target) {
        set<vector<int>> res;
        sort(nums.begin(),nums.end());
        int i=0,j=0;
        for(i=0;i<nums.size()-3;++i) 
        {
            for(j=i+1;j<nums.size()-2);++j) 
            {
                int left=j+1,right=nums.size()-1;
                while(left<right)
                {
                    int sum=nums[i]+nums[j]+nums[left]+nums[right];
                    if(sum==target)
                    {
                        vector<int> out;
                        out.push_back(nums[i]);
                        out.push_back(nums[j]);
                        out.push_back(nums[left]);
                        out.push_back(nums[right]);
                        res.insert(out);
                        ++left; 
                        --right;
                    } 
                    else if(sum<target) ++left;
                    else --right;
                }
            }
        }
        return vector<vector<int> > (res.begin(), res.end());
    }
};
```

# Search for a Range
## 问题分析：
搜索一个范围,利用二分法分别找左右边界
## 编程实现:
```C++
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        int idx=search(nums,0,nums.size()-1,target);
        if(idx==-1)   return {-1,-1};
        int left=idx,right=idx;
        while(left>0&&nums[left-1]==nums[idx])  --left;
        while(right<nums.size()-1&&nums[right+1]==nums[idx])  ++right;
        return {left,right};
    }
    int search(vector<int>& nums, int left, int right, int target) {
        if(left>right)  return -1;
        int mid=left+(right-left)/2;
        if(nums[mid]==target)  return mid;
        else if(nums[mid]<target) return search(nums,mid+1,right,target);
        else return search(nums,left,mid-1,target);
    }
};
```
