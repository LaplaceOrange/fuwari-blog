---
title: "[OI] 各大排序算法模板"
published: 2026-02-01
description: "OI中各大排序算法的模板，包括冒泡排序，选择排序，插入排序，计数排序等。"
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

## 五、二叉树排序

### 代码

```cpp
#include <bits/stdc++.h>
using namespace std;
const int N = 1e5 + 5;
struct node
{
    int data;
    node *left, *right; // 左儿子和右儿子
};
void print(node *t) // 递归中序输出
{
    if (t == NULL)
        return;
    print(t->left);         // 左儿子
    cout << t->data << " "; // 输出
    print(t->right);        // 右儿子
}
int main()
{
    int n;
    cin >> n;
    int x;
    cin >> x;
    node *head = new node;
    head->data = x;
    head->left = NULL;
    head->right = NULL;
    for (int i = 2; i <= n; i++)
    {
        cin >> x;
        node *q = new node;
        q->data = x;
        q->left = NULL;
        q->right = NULL;
        node *p = head;
        while (p != NULL)
        {
            if (x <= p->data) // 小于等于就放到左儿子
            {
                if (p->left == NULL)
                {
                    p->left = q;
                    break;
                }
                else
                {
                    p = p->left;
                }
            }
            else // 大于就放到右儿子
            {
                if (p->right == NULL)
                {
                    p->right = q;
                    break;
                }
                else
                {
                    p = p->right;
                }
            }
        }
    }
    print(head); // 中序输出
    return 0;
}
```