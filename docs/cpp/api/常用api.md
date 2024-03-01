# 常用api

## 大小写转换

```cpp
// toupper(char c)  tolower(char c)
for (int i = 0; i < s.length(); i++)s[i] = toupper(s[i]);
for (int i = 0; i < s.length(); i++)s[i] = tolower(s[i]);
```




下面三个需要包含头文件`#include <cmath>`

## 浮点数的绝对值 

`double fabs(double x);`

## 浮点数向下取整
例如，floor(3.7) 将返回 3.0，floor(-2.5) 将返回 -3.0。

`double floor(double x);`

## 浮点数向上取整
例如，ceil(3.2) 将返回 4.0，ceil(-1.8) 将返回 -1.0。

`double ceil(double x);`