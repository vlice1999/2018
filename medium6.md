# Rotate Image
## 问题分析：
围绕中心数字位置进行90°旋转,分别计算新位置
## 编程实现：
```C++
 class Solution {
 public:
     void rotate(vector<vector<int>>& matrix) {
         int i=0,j;
         for(i=0;i<matrix.size()/2;i++)
         {
            for(j=i;j<matrix.size()-1-i;j++)
            {
                 int tmp=matrix[i][j];
                 matrix[i][j]=matrix[n-1-j][i];
                 matrix[n-1-j][i]=matrix[n-1-i][n-1-j];
                 matrix[n-1-i][n-1-j]=matrix[j][n-1-i];
                 matrix[j][n-1-i]=tmp;
             }
         }
     }
 };
 ```

# Group Anagrams
## 问题分析：
集中字符串中的错位词,将字符顺序重新排列看是否相同
## 编程实现：
```C++
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>> res;
        unordered_map<string, vector<string>> m;
        for(string str : strs)
        {
            string t=str;
            sort(t.begin(),t.end());
            m[t].push_back(str);
        }
        for(auto a : m) 
        {
            res.push_back(a.second);
        }
        return res;
    }
};
```
