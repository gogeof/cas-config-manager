## package
```cmd
mvn clean package
```

## run
```cmd
java -jar cas-management.war 
```

# linux use config, for latter windows follow
## install mongodb
```cmd
# download and untar
curl -O https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-3.0.6.tgz
tar -zxvf mongodb-linux-x86_64-3.0.6.tgz
# move to dest dir
sudo mv  mongodb-linux-x86_64-3.0.6/ /usr/local/mongodb
# edit sysconfig
vi /etc/profile
# add and make it works
export PATH=/usr/local/mongodb/bin:$PATH
source /etc/progile
```

## start and stop mongodb
```cmd
# start
mongod --dbpath ~/data
# stop
mongod --dbpath ~/data --shutdown
```

## create users of mongodb for cas-config account needed
```cmd
# start
>mongod --dbpath ~/data
# login
>mongo
# use admin database
>use admin
# add new admin user
>db.createUser({user: "admin",pwd: "123456",roles:[{role:"userAdminAnyDatabase", db: "admin" } ]})
# use cas-mongo-database database
>use cas-mongo-database
# add user
>db.createUser({user: "cas-config",pwd: "123456",roles: [ { role: "readWrite", db: "cas-mongo-database" }]})
# stop and then restart with auth
>mongod --dbpath ~/data --auth
```
