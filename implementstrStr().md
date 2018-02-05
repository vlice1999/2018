## 问题分析
#### 字符串匹配
实现strstr(). 返回needle在haystack中第一次出现的位置，如果needle不在haystack中，则返回-1
## 编程实现
```C++
class Solution {
public:
    int strStr(string haystack, string needle) {
        int i=0,j=1,num=0;
        if(needle.empty()) return 0;
        if(needle.size()>haystack.size()) return -1;
            for(i=0;i<haystack.size()-needle.size()+1;i ++)
            {
                if(needle[num]==haystack[i])
                {
                    for(j=1;j<needle.size();j ++)
                    {
                        if(needle[j]!=haystack[i+j])
                            break;
                    }
                    if(j==needle.size())
                    return i;
                }
            }
        return -1;
    }
};
```
## 总结体会
1. 暴力遍历直到将子串遍历完
2. 考虑空字符串和需判断字符串比总字符串长的情况
3. 理解：最后输出的是什么真的是纠结了好长时间,错误理解成输出子串元素的个数导致一直wrong。
