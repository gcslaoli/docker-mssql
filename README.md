# 使用docker部署MSSQL(Microsoft SqlServer)
github地址： https://github.com/GCSLaoLi/docker-mssql

gitee镜像： https://gitee.com/gcslaoli/docker-mssql

微软官方提供了MSSQL的docker镜像 https://hub.docker.com/_/microsoft-mssql-server
# 环境变量
## Environment Variables

You can use environment variables to configure SQL Server on Linux Containers.

`ACCEPT_EULA` confirms your acceptance of the [End-User Licensing Agreement](https://go.microsoft.com/fwlink/?linkid=857698).

`SA_PASSWORD` is the database system administrator (userid = 'sa') password used to connect to SQL Server once the container is running. Important note: This password needs to include at least 8 characters of at least three of these four categories: uppercase letters, lowercase letters, numbers and non-alphanumeric symbols.

`MSSQL_PID` is the Product ID (PID) or Edition that the container will run with. Acceptable values:

- Developer : This will run the container using the Developer Edition (this is the default if no MSSQL_PID environment variable is supplied)
- Express : This will run the container using the Express Edition
- Standard : This will run the container using the Standard Edition
- Enterprise : This will run the container using the Enterprise Edition
- EnterpriseCore : This will run the container using the Enterprise Edition Core : This will run the container with the edition that is associated with the PID

For a complete list of environment variables that can be used, refer to the documentation [here](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-configure-environment-variables?view=sql-server-2017).

# 命令
启动数据库
```sh
docker-compose -f "docker-compose.yml" up -d --build 
```
查看数据库日志
```sh
docker-compose -f 'docker-compose.yml' -p 'docker-mssql' logs -f --tail 1000
```
关闭数据库
```sh
docker-compose -f "docker-compose.yml" down
```

# 导入已有的数据库文件

```sql
EXEC sp_attach_db @dbname = 'mydbname',
@filename1 = '/initdb/mydbfile.mdf',
@filename2 = '/initdb/mydbfile.ldf'
GO
```