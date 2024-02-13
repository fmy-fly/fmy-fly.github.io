### **辗转相除法求gcd**
```cpp
int gcd(int a,int b) {
    return b == 0 ? a:gcd(b,a%b);
}

```
### **利用gcd求lcm**
```cpp
// 计算最小公倍数
int lcm(int a, int b) {
    return (a * b) / gcd(a, b);
}

```
