## 问题分析：
#### 字符串处理
数数并记录，生成序列中第n个字符串
## 编程实现：
```C++
class Solution {
public:
    string countAndSay(int n) {
        int count=1,i=1,j=1;
        string nums="1";
        for(i=1;i<n;++ i)
        {
            count=1;
            string temp="";
            for(j=1;j<nums.size();++ j)
            {
                if(nums[j]==nums[j-1])
                    ++count;
                else 
                {
                    temp=temp+(char)(count+'0')+nums[j-1];
                     count=1;
                }
            }
            nums=temp+(char)(count+'0')+nums[nums.size()-1];
        }
        return nums;
        
    }
};
```
## 总结体会：
1. 结果输出要求是字符串
2. 理解题意：找规律,从1开始到推到n
3. 细节问题：count的重置
