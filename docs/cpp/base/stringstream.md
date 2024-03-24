# stringstream

## 以空格分割字符串


```cpp
string s = "hello world hey brother manba out";
stringstream ss(s);
string word;
int cnt = 0;
while(ss >> word){
    cout << word << endl;
    cnt++;
}
cout << cnt << endl;


```
