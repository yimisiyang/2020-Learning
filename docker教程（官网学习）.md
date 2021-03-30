## 1.开始学习

```shell
docker run -d -p 80:80 docker/getting-started
docker run -dp 80:80 docker/getting-started
```

`-d` 后台运行；`-p 80:80` 将物理端口的80映射到内网的80端口；`docker/getting-started` 使用的docker镜像。

## 2.什么是容器

简而言之，容器就是孤立于本主机上其它进程之外的一个单一进程。这种孤立利用了Linux内核的命名空间和cgroups.Docker致力于让这些功能更加容易使用。

## 3.什么是容器镜像

当运行一个容器时，它使用一个独立的文件系统，该自定义文件系统由docker镜像提供，由于该镜像包含容器的文件系统，因此他一定包含运行一个应用的所有内容，包括依赖、配置、脚本、二进制等。这个镜像也包含该容器的其它配置，例如环境变量，默认运行命令和其它元数据。

## 4.构建容器镜像

### 1.获取App

从github上下载该内容，https://github.com/docker/getting-started

### 2.构建容器镜像

为了构建一个应用，通常使用一个 `Dockerfile` 

1.创建一个dockerfile文件

```shell
FROM node:12-alpine
WORKDIR /app
COPY ..
RUN yarn install --production
CMD["node","src/index.jx"] 
```

### 3.使用docker build 命令进行编译

```shell
docker build -t getting-started .
```

`-t` 参数：给容器起一个名字；`.`  该参数告诉Docker在当前文件夹下搜索dockerfile文件。

### 4.开启App容器

```shell
docker run -dp 3000:3000 getting-started
```

通过浏览器进入 `http://localhost:3000`

## 5.更新App容器

### 1.移除旧容器

```shell
# 查看运行的docker容器
docker ps
# 使用docker stop 命令停止运行的容器
docker stop <容器ID>
# 使用docker rm 命令移除旧版本的容器
docker rm <容器ID>
# 也可以强制停止并移除容器
docker rm -f <容器ID>
```

**提示：**也可以通过docker控制面板移除旧容器，`IP：9000`

### 2.更新新容器

对原有容器进行版本升级，再次编译并启动。

```shell
docker build -t getting-started .
docker run -dp 3000:3000 getting-started
```

## 6.共享我们的容器

1. 通过浏览器登陆你的Docker Hub 账户；

2. 点击 `Create Repository` 按钮，创建一个名为你构建容器名字的公有仓库；

3. 执行以下命令将容器推送到公有仓库。

   ```shell
   # 登陆docker hub
   docker login -u YOUR-USER-NAME
   # 通过docker tag命令给你的容器起一个新的名字
   docer tag 容器名 dockerhub用户名/容器名
   # 将容器通过docker push 命令推送到远程
   docker push dockerhub用户名/容器名
   ```

   ## 7.持续化我们的数据库

   **抛出问题：** 你是否注意到，我们每次启动容器的时候都会清除我们的代办列表。为什么会这样？让我们了解一下容器是如何工作的。

   ### 1.容器文件系统

   当运行一个容器的时候，它使用镜像中的各个层作为它的文件系统，每个容器获取它自己的“暂存空间”去创建 `/update/remove` 文件。任何更改都不会在其它容器中显示，除非他们公用一个镜像。

   #### 练习:

   创建两个容器并为每个容器创建一个文件，发现在一个容器中创建的文件在另一个容器中并不可用。

   1.启动一个 `Ubuntu` 容器然后创建一个文件命名为 `/data.txt` 生成一个1-10000之间的随机数；

   ```shell
   docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /date.txt && tail -f /dev/null"
   ```

   `&&` 是用来区分两个命令，第一个命令是生成一个随机数并写入 `/data.txt` ；第二个命令是监视一个文件并保持容器运行。

   2.验证我们可以通过 `exec` 查看容器的输出，命令如下；

   ```shell
   docker exec <容器id> cat /data.txt
   ```

   3.现在启动另一个Ubuntu容器（同一个镜像），我们看到并没有 `data.txt` 文件

   ```shell
   docker run -it ubuntu ls /
   ```

   4.删除第一个容器

   ```shell
   docker rm -f <容器ID>
   ```

   ### 2.容器卷

   从前面的实验，我们可以看出每个容器的启动都从镜像定义的地方启动，尽管容器可以创建，更新和删除文件，当容器删除的时候这些更改将会丢失并且所有容器都是孤立的，通过容器卷，我们可以改变这些。

   `容器卷`提供了连接容器的特定文件系统路径到主机的能力，如果一个文件夹在容器中挂载，更改该文件夹中的内容也会在主机中可见。如果我们通过重启容器挂载相同的目录，我们也会看到相同的文件。

   总共有两种卷挂载的方式，这两种都会用到，我们先讲 `named valumes` 。

   #### 持久化我们的数据

   默认情况下，app的数据存储在 SQLite数据库 `/etc/todos/todo.db` 

   ```shell
   # 1.创建docker卷(卷存放在/var/lib/docker/volumes/todo-db)
   docker volume create todo-db
   # 2.通过 -v 参数指定卷挂载，我们将使用具名卷挂载到/etc/todos
   docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
   # 3.容器启动后，通过web端添加一些数据列表
   # 4.使用docker ps 查容器id，使用docker rm -f <id> 删除容器，或者使用Dashboard删除。
   # 5.重启一个容器。
   ```

   #### 深入探讨容器卷
   
   有人会问，“当我们使用具名named volume 时，docker把我们的文件存放在哪里了？”，我们可以使用 `docker volume inspect` 命令。
   
   ```shell
   docker volume inspect <容器名>
   ```
   
   

















　

