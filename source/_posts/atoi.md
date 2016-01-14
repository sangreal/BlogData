title: atoi implementation
date: 12/07/2015
tags: C++
---

面试官至少会期待应聘都能够在不需要提示的情况下，考虑到输入的字符串中有非数字字符和正负号，要考虑到最大的正整数和最小的负整数以及溢出。同时面试试还期待应聘者能够考虑到当输入的字符串不能转换成整数时，应该如何做错误处理。

* 1、检查字符串是否为空

* 2、对非法输入，返回0，并设置全局变量

* 3、溢出

* 4、空字符串""

* 输入字符串只有"+"或"-"号

```cpp
long long StrToIntCore(const char* str, bool minus);

enum Status {kValid = 0, kInvalid};
int g_nStatus = kValid;

int StrToInt(const char* str)
{
    g_nStatus = kInvalid;
    long long num = 0;

    if(str != NULL && *str != '\0') 
    {
        bool minus = false;
        if(*str == '+')
            str ++;
        else if(*str == '-') 
        {
            str ++;
            minus = true;
        }

        if(*str != '\0') 
        {
            num = StrToIntCore(str, minus);
        }
    }

    return (int)num;
}

long long StrToIntCore(const char* digit, bool minus)
{
    long long num = 0;

    while(*digit != '\0') 
    {
        if(*digit >= '0' && *digit <= '9') 
        {
            int flag = minus ? -1 : 1;
            num = num * 10 + flag * (*digit - '0');

            if((!minus && num > 0x7FFFFFFF) 
                || (minus && num < (signed int)0x80000000))
            {
                num = 0;
                break;
            }

            digit++;
        }
        else 
        {
            num = 0;
            break;
        }
    }

    if(*digit == '\0') 
    {
        g_nStatus = kValid;
    }

    return num;
}
```
