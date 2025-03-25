# wsl配置代理
## 配置文件
打开C:\Users\fmy\.wslconfig 这个文件，然后改成以下内容即可
```bash
[wsl2]
networkingMode = mirrored
autoProxy = true
```

## 关闭windows防火墙
得把windows防火墙关闭
