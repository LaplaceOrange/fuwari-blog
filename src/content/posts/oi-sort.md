---
title: [OI] 各大排序算法模板
published: 2026-02-01
description: OI中各大排序算法的模板，包括冒泡排序，选择排序，插入排序，计数排序等。
tags: [OI, Template]
category: OI
draft: false
---
​
## 一、冒泡排序

[**OI Wiki介绍**](https://oi-wiki.org/basic/bubble-sort/ "OI Wiki介绍")
### 1. 升序排序

```cpp
#include <iostream>
using namespace std;
int a[10005];

void bubble_sort(int n)
{
    bool changed = true;
    while (changed)
    {
        changed = false;
        for (int i = 1; i < n; i++)
        {
            if (a[i] > a[i + 1])
            {
                swap(a[i], a[i + 1]);
                changed = true;
            }
        }
    }
}

int main()
{
    int n;
    cin >> n;
    for (int i = 1; i <= n; i++)
        cin >> a[i];
    bubble_sort(n);
    for (int i = 1; i <= n; i++)
        cout << a[i] << " ";
    return 0;
}
```
### 2. 降序排序

```cpp
#include <iostream>
using namespace std;
int a[10005];

void bubble_sort(int n)
{
    bool changed = true;
    while (changed)
    {
        changed = false;
        for (int i = 1; i < n; i++)
        {
            if (a[i] < a[i + 1])
            {
                swap(a[i], a[i + 1]);
                changed = true;
            }
        }
    }
}

int main()
{
    int n;
    cin >> n;
    for (int i = 1; i <= n; i++)
        cin >> a[i];
    bubble_sort(n);
    for (int i = 1; i <= n; i++)
        cout << a[i] << " ";
    return 0;
}
```
## 二、选择排序

[**OI Wiki介绍**](https://oi-wiki.org/basic/selection-sort/ "OI Wiki介绍")
### 1. 升序排序

```cpp
#include <iostream>
using namespace std;
int a[10005];

void selection_sort(int n)
{
    for (int i = 1; i < n; i++)
    {
        int pos = i;
        for (int j = i + 1; j <= n; j++)
        {
            if (a[j] < a[pos])
                pos = j;
        }
        swap(a[i], a[pos]);
    }
}

int main()
{
    int n;
    cin >> n;
    for (int i = 1; i <= n; i++)
        cin >> a[i];
    selection_sort(n);
    for (int i = 1; i <= n; i++)
        cout << a[i] << " ";
    return 0;
}
```
### 2. 降序排序

```cpp
#include <iostream>
using namespace std;
int a[10005];

void selection_sort(int n)
{
    for (int i = 1; i < n; i++)
    {
        int pos = i;
        for (int j = i + 1; j <= n; j++)
        {
            if (a[j] > a[pos])
                pos = j;
        }
        swap(a[i], a[pos]);
    }
}

int main()
{
    int n;
    cin >> n;
    for (int i = 1; i <= n; i++)
        cin >> a[i];
    selection_sort(n);
    for (int i = 1; i <= n; i++)
        cout << a[i] << " ";
    return 0;
}
```

##  三、插入排序

[**OI Wiki介绍**](https://oi-wiki.org/basic/insertion-sort/ "OI Wiki介绍")
### 1. 升序排序
```cpp
#include <iostream>  
using namespace std;  
int a[10005];  
void insertion_sort(int n) {  
    for (int i = 1; i < n; ++i) {  
        int key = a[i];  
        int j = i - 1;  
        while (j >= 0 && a[j] > key) {  
            a[j + 1] = a[j];  
            j--;  
        }  
        a[j + 1] = key;  
    }  
}
int main()  
{  
    int n;  
    cin >> n;  
    for (int i = 1; i <= n; i++)  
        cin >> a[i];  
    insertion_sort(n);  
    for (int i = 1; i <= n; i++)  
        cout << a[i] << " ";  
    return 0;  
}
```
### 2. 降序排序
```cpp
#include <iostream>  
using namespace std;  
int a[10005];  
void insertion_sort(int n) {  
    for (int i = 1; i < n; ++i) {  
        int key = a[i];  
        int j = i - 1;  
        while (j >= 0 && a[j] > key) {  
            a[j + 1] = a[j];  
            j--;  
        }  
        a[j + 1] = key;  
    }  
}
int main()  
{  
    int n;  
    cin >> n;  
    for (int i = 1; i <= n; i++)  
        cin >> a[i];  
    insertion_sort(n);  
    for (int i = n; i >= 1; i++)  
        cout << a[i] << " ";  
    return 0;  
}
```


## 四、计数排序

[**OI Wiki介绍**](https://oi-wiki.org/basic/counting-sort/ "OI Wiki介绍")
### 1. 升序排序
```cpp
#include <iostream>  
using namespace std;  
int a[10005];  
int b[100005];  
  
void counting_sort(int n)  
{  
    for (int i = 1; i <= n; i++)  
        b[a[i]]++;  
}  
  
int main()  
{  
    int n, maxn = -1;  
    cin >> n;  
    for (int i = 1; i <= n; i++)  
    {  
        cin >> a[i];  
        maxn = max(maxn, a[i]);  
    }  
    counting_sort(n);  
    for (int i = 1; i <= maxn; i++)  
        while (b[i]--)  
            cout << i << " ";  
    return 0;  
}
```
### 2. 降序排序
```cpp
#include <iostream>  
using namespace std;  
int a[10005];  
int b[100005];  
  
void counting_sort(int n)  
{  
    for (int i = 1; i <= n; i++)  
        b[a[i]]++;  
}  
  
int main()  
{  
    int n, maxn = -1;  
    cin >> n;  
    for (int i = 1; i <= n; i++)  
    {  
        cin >> a[i];  
        maxn = max(maxn, a[i]);  
    }  
    counting_sort(n);  
    for (int i = maxn; i >= 1; i++)  
        while (b[i]--)  
            cout << i << " ";  
    return 0;  
}
```
