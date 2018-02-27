# Permutations
## 问题分析：
求全排列利用递归从头开始循环
## 编程实现：
```C++
class Solution {
public:
    vector<vector<int> > permute(vector<int> &num) {
        vector<vector<int> > res;
        vector<int> out;
        vector<int> visited(num.size(),0);
        permuteDFS(num,0,visited,out,res);
        return res;
    }
    void permuteDFS(vector<int> &num, int level, vector<int> &visited, vector<int> &out, vector<vector<int> > &res) {
        if (level == num.size()) res.push_back(out);
        else {
            for(int i=0;i<num.size();++i)
            {
                if(visited[i]==0) 
                {
                    visited[i]=1;
                    out.push_back(num[i]);
                    permuteDFS(num,level+1,visited,out,res);
                    out.pop_back();
                    visited[i]=0;
                }
            }
        }
    }
};
```

# Permutations II
## 问题分析：
避免输出的排列中有重复的产生
## 编程实现：
```C++
class Solution {
public:
    vector<vector<int> > permuteUnique(vector<int> &num) {
        vector<vector<int> > res;
        vector<int> out;
        vector<int> visited(num.size(), 0);
        sort(num.begin(), num.end());
        permuteUniqueDFS(num,0,visited,out,res);
        return res;
    }
    void permuteUniqueDFS(vector<int> &num, int level, vector<int> &visited, vector<int> &out, vector<vector<int> > &res) {
        if(level >= num.size()) res.push_back(out);
        else {
            for(int i=0;i<num.size();++i)
            {
                if(visited[i]==0)
                {
                    if(i>0&&num[i]==num[i-1]&&visited[i-1]==0) continue;
                    visited[i]=1;
                    out.push_back(num[i]);
                    permuteUniqueDFS(num,level+1,visited,out,res);
                    out.pop_back();
                    visited[i]=0;
                }
            }
        }
    }
};
```
