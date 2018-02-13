# Two Sum II - Input array is sorted
## 问题分析：
循环容易导致超时,所以用两个指针进行定位。
## 编程实现：
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int i=0,j=numbers.size()-1;
        while (i<j) 
      {
            if(numbers[i]+numbers[j]==target) return {i+1,j+1};
            else if (numbers[i]+numbers[j]<target) ++i;
            else --j;
        }
        return {i+1,j+1};
    }
};
```

# Excel Sheet Column Title
## 问题分析：
10进制数转换为26进制的数
## 编程实现：
```C++
class Solution {
public:
    string convertToTitle(int n) {
        string ret = "";
        while(n)
        {
            ret = (char)((n-1)%26+'A') + ret;
            n = (n-1)/26;
        }
        return ret;
    }
};
```
