# Postgers 12 and pgadmin4



It's a docker-compose file containing 2 services:
```
$ docker-compose ps
       Name                      Command               State               Ports             
---------------------------------------------------------------------------------------------
basic_pgadmin_1       /entrypoint.sh                   Up      443/tcp, 0.0.0.0:11111->80/tcp
basic_postgres_1      docker-entrypoint.sh postgres    Up      0.0.0.0:5432->5432/tcp        
```



### To launch
```
$ docker-compose up -d --build
```



### To shutdown
```
$ docker-compose down
```



# Web services
- [pgadmin](http://localhost:11111)
    User: test1234@test.com\
    Password: test1234



# sevrers.json
servers.json is meant for importing/exporting db servers setup into pgadmin

To export servers.json
```
$ docker exec -it postgres12-pgadmin4_pgadmin_1 python ./setup.py --dump-servers /tmp/servers.json --user test1234@test.com
$ docker exec -it postgres12-pgadmin4_pgadmin_1 cat /tmp/servers.json
``` 

To import servers.json mount servres.json to /pgadmin4/servers.json

