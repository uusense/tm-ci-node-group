# TestMan 持续集成组件服务



## Deploy


```
git clone https://git.uusense.cn/testman/tm-ci-node-group.git
cd tm-ci-node-group
docker-compose up -d
```
> 启动服务前，注意修改目录下的.env的配置参数。
> 服务启动后，在TestMan后台持续集成模块添加相应的Jenkins服务器与节点即可使用。
>
> 执行机节点因需要使用jactl命令工具，需要TestMan配置服务地址。



# 说明

1. 该组件包含1个Jenkins节点，服务端口与**Tunnel**端口分别是18080/19081登录的用户名与密码：uadmin/uusense
2. 该组件包含1个MinIO对象存储服务，API服务端口是19082，管理平台端口是19083，默认用户密码是uusense/uusense^123。服务部署成功后，登录管理平台端口添加相应的Bucket后，并在TestMan后台的持续集成管理模块里的配置页面配置好MinIO的相应配置。
3. 该组件包含1个Java环境的执行机节点，默认端口19084。 通过`ssh root@x.x.x.x`登录，密码是uusense。



# 执行机节点jactl安装说明

1. 通过后台的curl 命令可以执行机节点一键安装jactl命令行工具，jactl负责执行机与持续集成后台的任务与数据状态通讯，是必须组件。如果使用docker执行机，docker exec进到容器里部署好jactl后再导出这个容器为新的镜像，重新跑一个新的容器来做为执行机。
