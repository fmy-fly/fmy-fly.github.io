# string的api

## 1.find()
`size_t find(const string& str) const;`


带起始位置的形式：find() 函数接受两个参数，第一个参数是要查找的子字符串，第二个参数是起始搜索位置。
`size_t find(const string& str, size_t pos) const;`
```cpp
string s = "abcda";
cout << s.find('a') << endl;
cout << s.find('a',2)<< endl;
cout << (s.find("e") == string::npos) << endl;
//如果没找到返回string::npos

```
![alt text](image.png)


## 2.substr()
`string substr(size_t pos = 0, size_t len = npos) const;`


```cpp
string str = "Hello, World!";

// 从位置 7 开始提取子字符串，包括位置 7 的字符
string sub1 = str.substr(7);
cout << "sub1: " << sub1 << std::endl; // Output: World!

// 从位置 7 开始提取子字符串，提取 5 个字符
string sub2 = str.substr(7, 5);
cout << "sub2: " << sub2 << std::endl; // Output: World
```

## 3.replace()

```cpp
string str = "Hello, world!";
str.replace(7, 5, "everyone"); //第一个参数是起始位置，第二个参数是长度
cout << str << endl;  // 输出：Hello, everyone!
```



## 4.erase()
```cpp
string s = "abcdef";
s.erase(4,1); //第一个参数是起始位置，第二个参数是长度
cout << s << endl;
s.erase(1); //从这个位置开始全部删除
cout << s << endl;
```
