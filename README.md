## 打包

```cmd
mvn clean package
```

## 运行
```cmd
java -jar cas-management.war 
```

## 对接mongodb后需要创建cas-config需要的账户
```cmd
#启动
>mongod

#登录
>mongo

#切换数据库
>use admin

#新增管理员
>db.createUser({user: "admin",pwd: "123456",roles:[{role:"userAdminAnyDatabase", db: "admin" } ]})

#切换数据库
>use cas-mongo-database

# 新增用户
>db.createUser({user: "cas-config",pwd: "123456",roles: [ { role: "readWrite", db: "cas-mongo-database" }]})

#重启并开启认证
>mongod --auth
```
