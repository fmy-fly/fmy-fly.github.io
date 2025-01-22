# 单机配置集群redis
## windows配置多个redis端口
1. 复制redis文件夹多份
2. 修改两个配置文件中的端口号，改成对应的，全局替换。
分别是redis.windows.conf、redis.windows-service.conf
3. 在对应文件夹中注册服务
```bash
// 安装Redis服务
redis-server --service-install redis.windows.conf --service-name redis-xxxx --loglevel verbose
// 启动Redis服务
redis-server --service-start --service-name redis-xxxx
// 或者用这个启动
redis-server --port xxxx 
// xxxx 为端口号
```
4. 进入redis 命令行界面
```bash
redis-cli -p xxxx
// xxxx 为端口号
```
