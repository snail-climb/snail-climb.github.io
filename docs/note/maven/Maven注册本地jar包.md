# Maven注册本地jar包

```shell
mvn install:install-file -Dfile=jar文件的绝对地址 -DgroupId=组ID -DartifactId=工件ID -Dversion=版本号 -Dpackaging=jar
```

