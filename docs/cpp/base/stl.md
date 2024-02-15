### **1.string**
```cpp
    string str;
    str = "123123";
    int pos = str.find("4"); // - 1表示未找到
    int posr = str.rfind("4"); // rfind是查找最后一次匹配的位置,find是第一次
    str.replace(1, 3, "1111"); //替换的起始位置和结束位置
    str.insert(1, "111"); //从1号位置开始插入
    str.erase(1, 3);  //1号位置开始的3个字符删除
    string subStr = str.substr(1, 3); // 获取1号位置到3号位置的子串
    //可以省略结束位置参数，表示到结尾
    subStr = str.substr(1);
```
### **2.pair**
```cpp
    pair<string,int> pair1("1",2); //初始化
    cout  << pair1.first << " " << pair1.second<< endl;
    //第一个元素first 第二个元素second
```

### **3.vector**
```cpp
    vector<int> v;
    v.push_back(1); // 存放数据
    //v[i]进行索引
    //v.begin()返回迭代器，这个迭代器指向容器中第一个数据
    //v.end()返回迭代器，这个迭代器指向容器元素的最后一个元素的下一个位置
    //遍历
    for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
        cout << *it << endl;
    }
```

### **4.deque**

```cpp
   deque<int> d;
   d.push_back(10);  //后插
   d.push_front(10); //前插
   d.pop_back(); //后删
   d.pop_front();//前删
   //d[i] 支持随机访问
   //遍历
   for (deque<int>:: const_iterator it = d.begin(); it != d.end(); it++) {
        cout << *it << " ";

   }
```


### **5.stack**

```cpp
    stack<int> s;
    s.push(10); //入栈
    s.pop();    //出栈
    s.top();   //获取栈顶元素
```
### **6.queue**
```cpp
    queue<int> q;
    q.push(1); // 入队
    int front = q.front(); //获取队首元素
    int back = q.back(); //获取队尾元素
    q.pop(); // 出队
```

### **7.priority_queue**
```cpp
    priority_queue<int> pq;
    // 插入元素
    pq.push(10);
    // 删除元素
    pq.pop();
    //获取队首元素
    int a = pq.top();
    //遍历
    while (!pq.empty()) {
        cout << pq.top() << " "; // 输出队首元素
        pq.pop(); // 删除队首元素
    }
```

### **8.list**

```cpp
bool myCompare(int a, int b){
    return a >= b;
}
int main(){
    //链表
    list<int> list1;
    list1.push_front(1);
    list1.push_back(2);
    list1.pop_back();
    list1.pop_front();
    //排序
    list1.sort(); //默认的排序规则 从小到大
    list1.sort(myCompare); //自定义排序规则

    //list1.front(); 返回第一个元素
    //list1.back(); 返回最后一个元素
    return 0;
}
```
### **9.set/multiset**

- 底层结构是二叉树实现（复杂度:logN）  

**set和multiset区别**

- set不允许容器中有重复的元素
- multiset允许容器中有重复的元素

```cpp
    set<int> s;
    s.insert(1);
    s.insert(2); // 插入
    s.erase(2); // 删除
    int num = s.count(2); // 查询元素个数
    //时间复杂度为O(log2N)，红黑树实现
```
### **10.map/multimap**
* map中所有元素都是pair
* pair中第一个元素为key，第二个元素为value
* 所有元素都会根据元素的键值自动排序
* 底层结构是用二叉树实现

**map和multimap区别**

- map不允许容器中有重复的元素
- multimap允许容器中有重复的元素
```cpp
    //红黑树
    map<string, int> m;
    m.insert({"1",10});
    cout << m["1"]<<endl;
    m.erase("1");

```




### **11.unordered_set**
```cpp
    unordered_set<int> set ;
    set.insert(1); //插入
    set.erase(1);  //删除
    cout << set.count(1) << endl;
```

### **12.unordered_map**
```cpp
    unordered_map<int, int> m;
    m[2] = 1; // 插入
    m.insert(pair<int,int>(1,1));
    // 删除键值对
    m.erase(1);
    //遍历
    for (const auto& pair : m) {
        std::cout << "Key: " << pair.first << ", Value: " << pair.second << std::endl;
    }
    //是否存在
    int a = m.count(1);

```


### **13.公共方法**
- 返回容器中元素的数量:size() 
- 返回容器是否为空:empty()
- 遍历容器：
```cpp
 for ( 不同类型 <int>:: const_iterator it = d.begin(); it != d.end(); it++) {
        cout << *it << " ";
    }
```





