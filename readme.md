
### phper 常用环境构建

- - -

不熟悉 docker 戳这里 [入门到实践](https://yeasy.gitbooks.io/docker_practice/)

### 使用

#### env

```
// 确保 env 文件中指定的路径，已在宿主机中创建
mv env-example .env
```

#### 启动

```
// php-fpm 会从依赖中启动
docker-compose up -d nginx mysql redis
```

#### 配置站点

复制 `./nginx/conf.d/default.conf` 进行自定义配置，若 nginx 容器存在，需执行 `docker-compose restart nginx`

#### 注意

1. 修改 `Dockerfile` `env` `docker-compose.yml` 文件后，需要删除对应服务容器，再重新构建镜像。
2. php-fpm 目录中 `php.ini` 文件目前仅提供了 `7.2` 版本，若使用其他版本 php 请自行添加配置文件，请遵循 `php<PHP_VERSION>.ini` 命名规则，PHP_VERSION 为 env 中指定配置。
