# Set Matrix Zeroes
## 问题分析：
矩阵赋零,利用原数组来记录各行各列是否有0,然后不断遍历
## 编程实现：
```C++
class Solution {
public:
    void setZeroes(vector<vector<int> > &matrix) {
        if (matrix.empty() || matrix[0].empty()) return;
        int m = matrix.size(), n = matrix[0].size();
        bool rowZero = false, colZero = false;
        int i=0,j=0,k=1,x=1;
        for(i=0;i<m;++i)
        {
            if(matrix[i][0]==0) 
            colZero=true;
        }
        for(j=0;j<n;++j) 
        {
            if(matrix[0][j]==0) 
            rowZero=true;
        } 
        for(k=1;k<m;++k)
        {
            for(x=1;x<n;++x) 
            {
                if (matrix[k][x] == 0)
                {
                    matrix[0][x] = 0;
                    matrix[k][0] = 0;
                }
            }
        }
        for(int i=1;i<m;++i)
        {
            for (int j=1;j<n;++j)
            {
                if(matrix[0][j]==0 || matrix[i][0]==0)
                {
                    matrix[i][j]=0;
                }
            }
        }
        if (rowZero)
        {
            for(int i=0;i<n;++i) 
            matrix[0][i]=0;
        }
        if(colZero) 
        {
            for(int i=0;i<m;++i) 
            matrix[i][0]=0;
        }
    }
};
```

# Sort Colors
## 问题分析：
颜色排序,遍历数组分别记录个数然后更新赋值
## 编程实现：
```C++
class Solution {
public:
    void sortColors(int A[], int n) {
        int count[3]={0},idx=0;
        for(int i=0;i<n;++i) 
        ++count[A[i]];
        for(int i=0;i<3;++i)
        {
            for(int j=0;j<count[i];++j)
            {
                A[idx++]=i;
            }
        }
    }
};
```
