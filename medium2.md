# Integer to Roman
## 问题分析：
整数转换为罗马数字,是 Roman to Integer的类似题目,基本算法相同,分离各个位然后分别别表示
## 编程实现：
```C++
class Solution {
public:
    string intToRoman(int num) {
        string res="";
        char roman[]={'M','D','C','L','X','V','I'};
        int value[]={1000,500,100,50,10,5,1};
        int n=0,i=1,j=6;
        for(n=0;n<7;n+=2)
        {
            int x=num/value[n];
            if (x < 4)
            {
                for(i=1;i<=x;++i)
                res += roman[n];
            }
            else if(x==4)   
            res+=roman[n]+roman[n-1];
            else if (x>4&&x<9) 
            {
                res+=roman[n-1];
                for(j=6;j<=x;++j) 
                res+=roman[n];
            }
            else if(x==9) 
            res+=roman[n]+roman[n-2];
            num%=value[n];            
        }
        return res;
    }
};
```

# Divide Two Integers
## 问题分析：
两数相除但是不能使用除法乘法和取余运算,根据除法的基本原理结合递归,注意最后返回值的正负问题
## 编程实现：
```C++
class Solution {
public:
    int divide(int dividend, int divisor) {
        long long res=0;
        long long m=abs((long long)dividend),n=abs((long long)divisor);
        long long t=n,p=1;
        if(m<n) return 0;
        while(m>(t<<1)) 
        {
            t<<=1;
            p<<=1;
        }
        res+=p+divide(m-t,n);
        if((dividend<0)^(divisor<0))
        res=-res;
        return res>INT_MAX ? INT_MAX : res;
    }
};
```
