# sort

## 容器
```cpp
vector<int> v = {3, 1, 4, 1, 5, 9, 2, 6}; // 创建一个整型向量

// 使用 std::sort 对向量进行升序排序
sort(v.begin(), v.end());
```

## 数组
```cpp
int a[5] ={1,2,3,4,5};
sort(a,a + 5);
```

## 自定义排序
```cpp
 sort(rec.begin(), rec.end(), [](const vector<int>& a, const vector<int>& b) {
            return a[0] > b[0];  // 降序排列，如果需要升序，将 `>` 改为 `<`
    });
```