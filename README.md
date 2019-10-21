### 项目地址：
https://github.com/aimerforreimu/auxpi

### 启动容器
```
docker run -itd --restart always --name Auxpi -p 2333:2333 orangeqiu/auxpi
```
另可将数据库以及配置文件映射到宿主机自定义目录下（推荐：方便后边操作数据库以及修改配置文件）：
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
- 首先删除数据库文件，并进入容器：

```
 docker exec -it Auxpi /bin/bash
```

- 然后初始化程序：

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
- 紧接着创建数据库：

```
./auxpi migrate
```
成功后会提示：
```
   _       __  __  ___ _____
  /_\  /\ /\ \/ / / _ \\_   \
 //_\\/ / \ \  / / /_)/ / /\/
/  _  \ \_/ /  \/ ___/\/ /_
\_/ \_/\___/_/\_\/   \____/

🍭 A NEW API IMAGES STORE TOOL 🍭

......

[INFO]: Migrate done
```
- 最后，创建管理员：

```
./auxpi -mod=admin -name=hello -email=auxpi@0w0.tn -pass=123123123
```
这样就可以创建一个 密码为：123123123 用户名为：hello 邮箱为：auxpi@0w0.tn 的管理员账号，管理员有且只有一个，并且用户 ID 只能为1

成功后同样会返回如下信息：
```
   _       __  __  ___ _____
  /_\  /\ /\ \/ / / _ \\_   \
 //_\\/ / \ \  / / /_)/ / /\/
/  _  \ \_/ /  \/ ___/\/ /_
\_/ \_/\___/_/\_\/   \____/

🍭 A NEW API IMAGES STORE TOOL 🍭

......

[INFO]: Create Admin SUCCESS
```
