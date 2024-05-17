# php-fpm 7.4 版本镜像

> php-fpm + supervisor


## 命令

构建

```shell
docker build -t qq237661791/php74zhibang:latest .
```

启动

```shell
docker run -d --name php74 qq237661791/php74zhibang
```



推送

```shell
docker push qq237661791/php74zhibang:latest
```


## debug

```shell
docker-compose -d
```
