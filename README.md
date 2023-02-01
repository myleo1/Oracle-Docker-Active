# Oracle-Docker-Active

应对甲骨文免费机器回收机制，基于alpine的Docker"锻炼"镜像

使用stress-ng生成CPU压力

## 思路

95%的 CPU 利用率低于 10%

网络利用率低于10%

内存利用率低于 10% （仅适用于ARM机型）

================================================

对于ARM机型，能占用内存的，尽量占用内存为10%以上即可

对于AMD机型，7天内5%以上时间CPU利用率高于10%即可

由于stress-ng调用内存压力测试时，会产生比较大的CPU负载，而ARM机型需要一直保持内存在10%以上，故本镜像对于ARM机型暂时也统一使用CPU占用来解决活跃度问题

## 开始锻炼

此Docker镜像将会在北京时间凌晨3点20分开始占用15%左右的CPU资源，一直持续1.5小时来满足CPU占用的要求

对于ARM机型：

```bash
docker run -d --name oracle-active --restart=always myleo1/oracle-docker-active:arm64
```

对于AMD机型：

```bash
docker run -d --name oracle-active --restart=always myleo1/oracle-docker-active:amd64
```

## 取消锻炼

```bash
docker rm -f oracle-active
```

对于ARM机型：

```bash
docker rmi myleo1/oracle-docker-active:arm64
```

对于AMD机型：

```bash
docker rmi myleo1/oracle-docker-active:amd64
```



## 日志查看/锻炼情况查看

```bash
docker logs -f --tail=50 oracle-active
```

