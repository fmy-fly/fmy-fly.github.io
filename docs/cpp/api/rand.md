取随机数
```cpp
//需要包含头文件#include <cstdlib>,<ctime>
int main()
{
    srand((time(nullptr))); // 设置随机数种子
    int a = rand(); // 0 - 65535
    int randomNumber = rand() % 13 + 1; //生成1-13的随机数
}
```