# Docker for MacOS

### 1. 安装docker
`brew install docker`

### 2. 安装[___colima___](https://github.com/abiosoft/colima)
`brew install colima` <br>
`colima start`

# Container for Mysql
### 3. 新建容器
```shell
docker run --name mysql -e MYSQL_ROOT_PASSWORD=dev -p 3306:3306 -d mysql:5.7 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```

### 4. 查看所有容器
`docker ps -a`

### 5. 启动容器
`docker start <CONTAINER ID>`

### 6. 重启容器
`docker restart <CONTAINER ID>`

### 7. 进入容器
`docker attach <CONTAINER ID>` <br>
`docker exec <CONTAINER ID>`

### 8. 停止容器
`docker stop <CONTAINER ID>`

### 9. 删除容器
`docker rm -f <CONTAINER ID>`
