# 字符数组和cpp字符串之间的转换

## 字符串转字符数组
```cpp
//第一种
string str = "Hello";
char cstr[str.size() + 1]; 
strcpy(cstr, str.c_str()); 


//第二种
string str = "Hello";
const char* cstr = str.c_str(); // 使用c_str()方法
```

## 字符数组转字符串
```cpp
char s2 [] = "abc";
string t1;
t1 = s2
```


## char * 与char []的转换

```cpp
char str[] = "example";
char *ptr = str; // 直接将数组名赋给指针即可






const char *ptr = "example";
int len = strlen(ptr);
char arr[len + 1]; // 需要额外的空间来存储字符串的拷贝以及终止符 '\0'
strcpy(arr, ptr);
```