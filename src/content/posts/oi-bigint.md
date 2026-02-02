---
title: "[OI] 高精度计算模板”
published: 2026-02-01
description: "OI中高精度计算的模板，包括大整数的加减乘除模等。"
tags: [OI, Template]
category: OI
draft: false
---

## 完整代码

**洛谷例题请出门左转: ** [**P1932**](https://www.luogu.com.cn/problem/P1932)

**AC记录: ** [**R260290757**](https://www.luogu.com.cn/record/260290757)

```cpp
#include <bits/stdc++.h>
using namespace std;
const int N = 2e4 + 5;

struct Bigint
{
    int len, a[N];
    Bigint(string x = "0")
    {
        memset(a, 0, sizeof(a));
        int start = 0;
        while (start < (int)x.size() - 1 && x[start] == '0')
            start++;

        len = x.size() - start;
        for (int i = 0; i < len; i++)
        {
            a[i + 1] = x[x.size() - 1 - i] - '0';
        }
    }
    int &operator[](int i)
    {
        return a[i];
    }
    void flatten(int L)
    {
        len = L;
        for (int i = 1; i <= len; i++)
        {
            a[i + 1] += a[i] / 10;
            a[i] %= 10;
        }
        for (; !a[len];)
            len--;
    }
    void print()
    {
        for (int i = max(len, 1); i >= 1; i--)
        {
            cout << a[i];
        }
    }
};

bool operator>=(Bigint a, Bigint b)
{
    if (a.len != b.len)
        return a.len > b.len;
    for (int i = a.len; i >= 1; i--)
        if (a[i] != b[i])
            return a[i] > b[i];
    return true;
}

Bigint operator+(Bigint a, Bigint b)
{
    Bigint c;
    int len = max(a.len, b.len);
    for (int i = 1; i <= len; i++)
    {
        c[i] += a[i] + b[i];
    }
    c.flatten(len + 1);
    return c;
}
Bigint operator*(Bigint a, Bigint b)
{
    Bigint c;
    int lena = a.len, lenb = b.len;
    for (int i = 1; i <= lena; i++)
    {
        for (int j = 1; j <= lenb; j++)
        {
            c[i + j - 1] += a[i] * b[j];
        }
    }
    c.flatten(lena + lenb + 11);
    return c;
}

Bigint operator-(Bigint a, Bigint b)
{
    Bigint c;
    int len = a.len;
    for (int i = 1; i <= len; i++)
    {
        if (a[i] < b[i])
        {
            a[i] += 10;
            a[i + 1]--;
        }
        c[i] = a[i] - b[i];
    }
    c.flatten(len);
    return c;
}

Bigint operator/(Bigint a, Bigint b)
{
    Bigint rem = Bigint("0");
    string ans = "";
    for (int i = a.len; i >= 1; i--)
    {
        rem = rem * Bigint("10");
        rem[1] += a[i];
        rem.flatten(rem.len + 2);
        int cnt = 0;
        while (rem >= b)
        {
            rem = rem - b;
            cnt++;
        }
        ans += char(cnt + '0');
    }
    int start = 0;
    while (start < (int)ans.size() - 1 && ans[start] == '0')
        start++;
    return Bigint(ans.substr(start));
}

Bigint operator%(Bigint a, Bigint b)
{
    return a - ((a / b) * b);
}

int main()
{
    string a, b;
    cin >> a >> b;
    Bigint x(a), y(b);
    (x + y).print();
    cout << endl;

    if (x >= y)
    {
        (x - y).print();
    }
    else
    {
        cout << '-';
        (y - x).print();
    }
    cout << endl;

    (x * y).print();
    cout << endl;
    (x / y).print();
    cout << endl;
    (x % y).print();
    cout << endl;
    return 0;
}
```

**PS: 目前Bigint模板只支持正数**