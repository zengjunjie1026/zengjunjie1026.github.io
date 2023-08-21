---
title: mongodb新建用户
date: 2023-08-22 07:27:40
tags: server
---

```bash
db.createUser({ 
    user: "admin", 
    pwd: "---------", 
    roles: [ { role: "root", db: "admin" } ], 
    mechanisms : ["SCRAM-SHA-1"] 
})
```


1. 登录数据库

```

/path/mongo  --host=172.16.218.27 --port=27017 -u username  -p 'XXX'  --authenticationDatabase=admin

```


2. 查看 admin库表

```
> use admin
> show tables

> show tables

system.users
system.version

```

3. 查看各表数据

```
> db.system.version.find().pretty()
{ "_id" : "featureCompatibilityVersion", "version" : "3.4" }
{ "_id" : "authSchema", "currentVersion" : 5 }

```

```
> use admin
> db.system.users.find().pretty()
{
        "_id" : "admin.superUser",
        "user" : "superUser",
        "db" : "admin",
        "credentials" : {
                "SCRAM-SHA-1" : {
                        "iterationCount" : 10000,
                        "salt" : "dBhasH+fHybp6BKy5sPJFw==",
                        "storedKey" : "6yQsEZsAt4PH6OO/jKMqLiIHTqg=",
                        "serverKey" : "6GDMJwJCZ833kP/jCdj0VKOd+k0="
                }
        },
        "roles" : [
                {
                        "role" : "root",
                        "db" : "admin"
                }
        ]
}
{
        "_id" : "testDB01.testUser01",
        "user" : "testUser01",
        "db" : "testDB01",
        "credentials" : {
                "SCRAM-SHA-1" : {
                        "iterationCount" : 10000,
                        "salt" : "Tu2bpckgHjP17nOc+s2fGA==",
                        "storedKey" : "LO+Tc7U6tz54e2NCsKM0O9+Z/uo=",
                        "serverKey" : "cXYjU54vGoLQ58ZpeWXzZ7ZeVgI="
                }
        },
        "roles" : [
                {
                        "role" : "readWrite",
                        "db" : "testDB01"
                },
                {
                        "role" : "dbAdmin",
                        "db" : "testDB01"
                },
                {
                        "role" : "userAdmin",
                        "db" : "testDB01"
                }
        ]
}
{
        "_id" : "testDB02.testUser02",
        "user" : "testUser02",
        "db" : "testDB02",
        "credentials" : {
                "SCRAM-SHA-1" : {
                        "iterationCount" : 10000,
                        "salt" : "a4PwETCeMojRGv3mNp5OsQ==",
                        "storedKey" : "xajSCeYddSMHn+Dtr3/+OzghGw8=",
                        "serverKey" : "J3WrHUIrxDgl0OfWw5kpXcthw/o="
                }
        },
        "roles" : [
                {
                        "role" : "readWrite",
                        "db" : "testDB02"
                },
                {
                        "role" : "dbAdmin",
                        "db" : "testDB02"
                },
                {
                        "role" : "userAdmin",
                        "db" : "testDB02"
                }
        ]
}


```


```
> use testDB
> db.createUser(
{
   user : "testUser",
   pwd : "Mongo@123",
   roles: [ { role : "readWrite", db : "testDB" } ,
            { role : "dbAdmin", db : "testDB" } ,
            { role : "userAdmin", db : "testDB" }  
          ]
   }
)


> db.system.users.find().pretty()

{
        "_id" : "testDB.testUser",
        "user" : "testUser",
        "db" : "testDB",
        "credentials" : {
                "SCRAM-SHA-1" : {
                        "iterationCount" : 10000,
                        "salt" : "a4PwETCeMojRGv3mNp5OsQ==",
                        "storedKey" : "xajSCeYddSMHn+Dtr3/+OzghGw8=",
                        "serverKey" : "J3WrHUIrxDgl0OfWw5kpXcthw/o="
                }
        },
        "roles" : [
                {
                        "role" : "readWrite",
                        "db" : "testDB"
                },
                {
                        "role" : "dbAdmin",
                        "db" : "testDB"
                },
                {
                        "role" : "userAdmin",
                        "db" : "testDB"
                }
        ]
}

 注： 在 testDB库创建，只对 testDB有读、写和管理权限，在testDB认证鉴权
```


```
> use admin
> db.createUser(
 {
    user : "testUser",
    pwd : "Mongo@123",
    roles: [ { role : "readWrite", db : "testDB" } ,
             { role : "dbAdmin", db : "testDB" } ,
             { role : "userAdmin", db : "testDB" }
           ]
    }
 )
Successfully added user: {
        "user" : "testUser",
        "roles" : [
                {
                        "role" : "readWrite",
                        "db" : "testDB"
                },
                {
                        "role" : "dbAdmin",
                        "db" : "testDB"
                },
                {
                        "role" : "userAdmin",
                        "db" : "testDB"
                }
        ]
}


> db.system.users.find().pretty()

{
        "_id" : "admin.testUser",
        "user" : "testUser",
        "db" : "admin",
        "credentials" : {
                "SCRAM-SHA-1" : {
                        "iterationCount" : 10000,
                        "salt" : "IzZhDiGBM7fvZ09Y99qY1Q==",
                        "storedKey" : "qbEWrB1xrV939z4vCxULiw7W2e4=",
                        "serverKey" : "vPZg8qrTGjnIHKouxf048Ci3Z/0="
                }
        },
        "roles" : [
                {
                        "role" : "readWrite",
                        "db" : "testDB"
                },
                {
                        "role" : "dbAdmin",
                        "db" : "testDB"
                },
                {
                        "role" : "userAdmin",
                        "db" : "testDB"
                }
        ]
}

注： 在 admin库创建，只对 testDB有读、写和管理权限，在admin认证鉴权
```

### 修改用户密码
```
/path/mongo  --host=172.16.218.27 --port=27017 -u username  -p 'XXX'  --authenticationDatabase=admin

# testDB.testUser
>  use testDB
>  db.changeUserPassword('testUser','newPasswd'))"

# admin.testUser
>  use admin
>  db.changeUserPassword('testUser','newPasswd'))"
```

### 删除用户
```
# testDB.testUser

/path/mongo  --host=172.16.218.27 --port=27017 -u username  -p 'XXX'  --authenticationDatabase=admin

# 通过用户所在库删除
>  use testDB
>  db.dropUser("testUser")

# 通过admin库删除
>  use admin
> db.system.users.remove({"_id":"testDB.testUser"})

```


### 客户端工程jdbc连接字符串示例

```
# authSource=testDB
spring.data.mongodb.uri=mongodb://${username}:${password}@xx.xx.xx.xx:27017,xx.xx.xx.xx:27017,xx.xx.xx.xx:27017/testDB?authSource=testDB&authMechanism=SCRAM-SHA-1
```

```
# authSource=admin
spring.data.mongodb.uri=mongodb://${username}:${password}@xx.xx.xx.xx:27017,xx.xx.xx.xx:27017,xx.xx.xx.xx:27017/testDB?authSource=admin&authMechanism=SCRAM-SHA-1
```

### 关于账号创建的注意事项：

1.  第一步新建一个超管账号 superUser(示例)，授予 mongoDB root 角色权限，密码跟其他账号都不一样

2. 为各业务库创建业务账号，尽量统一一个模块一个用户名/密码，不同模块用户名/密码不同

3. mongoDB的用户名是跟库走的  db.user ，在哪个库创建的用户就走哪个库做认证，要么统一走各自业务库创建、授权、认证鉴权，要么统一通过admin库

4. superUser(示例) 只能走admin做认证鉴权，是数据库的超级管理员

5. 修改用户和删除用户等，和创建用户一样，需要切换到数据库管理员的身份, 也就是需要先切换到admin库完成认证,，才能进行后面的操作. 

6. 删除用户可以在 admin 库删除，但是修改密码只能创建用户的对应库，用户是跟着库走的
