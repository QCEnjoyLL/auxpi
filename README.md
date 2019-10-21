### 项目地址：
https://github.com/aimerforreimu/auxpi

### 启动容器
```
docker run -itd --restart always --name Auxpi -p 2333:2333 orangeqiu/auxpi
```
另可将数据库以及配置文件映射到宿主机自定义目录下：
```
docker run -itd -v /opt/go/db:/opt/go/db -v /opt/go/conf:/opt/go/conf --restart always --name Auxpi -p 2333:2333 orangeqiu/auxpi
```
### 默认信息：
```
USERNAME=admin
EMAIL=auxpi@example.com
PASSWORD=12345678
 ```
 ### 修改默认配置：
- 首先进入容器

```
 docker exec -it Auxpi /bin/bash
```

- 删除db目录下的数据库文件。然后执行：

```
./auxpi init
```

可以看到以下信息：
```
   _       __  __  ___ _____
  /_\  /\ /\ \/ / / _ \\_   \
 //_\\/ / \ \  / / /_)/ / /\/
/  _  \ \_/ /  \/ ___/\/ /_
\_/ \_/\___/_/\_\/   \____/

🍭 A NEW API IMAGES STORE TOOL 🍭

[INFO]:AUXPI have already initialization complete.
[INFO]:Please run "./auxpi run"  to start 
```
- 再次使用命令：

```
./auxpi -mod=admin -name=xxx -email=xxxx@xxx.com -pass=xxxx
```
即可创建新的管理员
