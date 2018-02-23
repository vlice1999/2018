# Add Two Numbers
## 问题分析：
运用递归从末尾到首位进行相加
## 编程实现：
```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
         return helper(l1,l2,0);
    }
public ListNode helper(ListNode l1, ListNode l2, int carry){
        if(l1==null && l2==null)
        {
            return carry==0? null : new ListNode(carry);
        }
        if(l1==null && l2!=null){
            l1=new ListNode(0);
        }
        if(l2==null && l1!=null){
            l2=new ListNode(0);
        }
        int sum=l1.val+l2.val+carry;
        ListNode curr=new ListNode(sum%10);
        curr.next=helper(l1.next,l2.next,sum/10);
        return curr;
    }
};
```

#  Longest Substring Without Repeating Characters
## 问题分析：
求最长无重复字符串,建立数组记录所有字符,再遍历整个字符串
## 编程实现：
```C++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int m[256]={0},res=0,left=0;
        int i=0;
        for(i=0;i<s.size();++i) 
        {
            if (m[s[i]]==0||m[s[i]]<left)
            {
                res=max(res,i-left+1);
            } 
            else 
            {
                left=m[s[i]];
            }
            m[s[i]]=i+1;
        }
        return res;
    }
};
```
