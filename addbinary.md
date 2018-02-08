## 问题分析：
#### 二进制数相加
补全较短二进制字符串然后对应相加
## 编程实现：
```C++
class Solution {
public:
    string addBinary(string a, string b) {
        string res;
        int na = a.size();
        int nb = b.size();
        int n = max(na, nb);
        bool carry = false;
        if (na > nb) {
            for (int i = 0; i < na - nb; ++i) b.insert(b.begin(), '0');
        }
        else if (na < nb) {
            for (int i = 0; i < nb - na; ++i) a.insert(a.begin(), '0');
        }
        for (int i = n - 1; i >= 0; --i) {
            int tmp = 0;
            if (carry) tmp = (a[i] - '0') + (b[i] - '0') + 1;
            else tmp = (a[i] - '0') + (b[i] - '0');
            if (tmp == 0) {
                res.insert(res.begin(), '0');
                carry = false;
            }
            else if (tmp == 1) {
                res.insert(res.begin(), '1');
                carry = false;
            }
            else if (tmp == 2) {
                res.insert(res.begin(), '0');
                carry = true;
            }
            else if (tmp == 3) {
                res.insert(res.begin(), '1');
                carry = true;
            }
        }
        if (carry) res.insert(res.begin(), '1');
        return res;
    }
};
```
## 总结体会：
二进制数相加并且保存在string中需要考虑如何将string和int之间互相转换且每位相加时可能进位会影响相加的结果。

