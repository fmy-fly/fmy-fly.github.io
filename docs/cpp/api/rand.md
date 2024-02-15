取随机数
```cpp
int main()
{
    srand(time(nullptr)); // 设置随机数种子
    int a = rand(); // 0 - 65535
}
```