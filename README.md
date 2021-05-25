# Postgers 12 and pgadmin4



### Use-cases
- I'm a developer and need quckly postgres db with pgadmin



### Details
It's a docker-compose file containing next services:
```
$ docker-compose ps
  Name                Command              State               Ports             
---------------------------------------------------------------------------------
pgadmin    /entrypoint.sh                  Up      443/tcp, 0.0.0.0:11111->80/tcp
postgres   docker-entrypoint.sh postgres   Up      0.0.0.0:5432->5432/tcp 
```



### Cridentials
All cridentials to pg and pgadmin are located here in .env file\
If you want to change cridentials - simply edit .env



### Updating /etc/hosts
Here is a tool which uses docker events for updating /etc/hosts.\
Prior to launching docker-compose do this:
```
$ sudo apt update && sudo apt install jq
$ sudo bash ./docker-hosts-update.sh
```
Once this script is run it will append/remove entiries into /etc/hosts



#### Updating /etc/hosts(Option B)
```
$ echo "$(docker exec -it pgadmin sh -c "hostname -i" | head -c-2) $(docker exec -it pgadmin sh -c "hostname" | head -c-2)" | sudo tee -a /etc/hosts
$ echo "$(docker exec -it postgres sh -c "hostname -i" | head -c-2) $(docker exec -it postgres sh -c "hostname" | head -c-2)" | sudo tee -a /etc/hosts
```



### To launch
```
$ docker-compose up
```
Ensure /etc/hosts contains records for all containers



### To shutdown
```
$ docker-compose down
```



### Web services
- [localhost:11111](http://localhost:11111)\
    User: test1234@test.com\
    Password: test1234



### sevrers.json
servers.json is meant for importing/exporting db servers setup into pgadmin

To export servers.json
```
$ docker exec -it pgadmin python ./setup.py --dump-servers /tmp/servers.json --user test1234@test.com
$ docker exec -it pgadmin cat /tmp/servers.json
``` 

To import servers.json mount servres.json to /pgadmin4/servers.json


### Screenshots

#### Login page
<p align="center">
    <img width="900" height="600" src="pic1.png">
</p>
<br>



#### DB login
<p align="center">
    <img width="900" height="600" src="pic2.png">
</p>
<br>



#### DB view
<p align="center">
    <img width="900" height="600" src="pic3.png">
</p>
<br>

