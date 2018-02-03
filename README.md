## 问题分析
本题考查栈的用法,首先遍历输入字符串，如果当前字符为左半边括号时，则将其压入栈中；
如果遇到右半边括号时，若此时栈为空，则直接返回false，如不为空，则取出栈顶元素；
栈顶元素若为对应的左半边括号，则继续循环，反之返回false。
## 编程实现
```class Solution {
public:
    bool isValid(string s) {
        stack<char> parentheses;
        int i=0;
        for(i=0;i<s.size();++ i)
        {
            if(s[i]=='('||s[i]=='['||s[i]=='{')
                parentheses.push(s[i]);
            else 
            {
                if(parentheses.empty()) return false;
                if(s[i]==')'&&parentheses.top()!='(') return false;
                if(s[i]==']'&&parentheses.top()!='[') return false;
                if(s[i]=='}'&&parentheses.top()!='{') return false;
                parentheses.pop();
            }
        }
        return parentheses.empty();
    }
};
```
## 总结分析
栈是限定仅在表尾进行插入和删除操作的线性表，数据暂时存储的地方,允许在同一端进行插入和删除操作的特殊线性表.


