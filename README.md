# Zabbix_Guacd-docker
Docker compose that will bring up Zabbix server and Guacamole server to monitor a large scale environments


The docker compose contains
- Zabbix server
- Zabbix frontend
- Guacamole server
- Guacamole composer
- Guacamole frontend
- DB managing both servers

# Zabbix and Guacamole via compose
A simple project to automate deploying these 2 services while also modifying the postgres image to serve them both at the same time.

## How to use
Clone this repository
```bash
git clone -b zabbix+guacamole-compose https://github.com/Filip3Kx/DevOpsLearning
```
Go into the downloaded directory
```bash
cd DevOpsLearning
```

Run the [pepare.sh](https://github.com/Filip3Kx/Zabbix_Guacd-docker/blob/main/prepare.sh) script. This will create SSL certificates in a dir that will be later used by the containers
```bash
sudo bash prepare.sh
```
All that's left to do is run the compose file. **Be sure to stay in the same directory**
```bash
docker compose up -d
```
https://github.com/Filip3Kx/Zabbix_Guacd-docker/blob/main/docker-compose.yml
## Compose file
Using this [docker compose file](https://github.com/Filip3Kx/Zabbix_Guacd-docker/blob/main/docker-compose.yml) will deploy containers running
- Zabbix server
- Zabbix frontend
- Guacamole server
- Guacamole composer
- Guacamole frontend
- DB managing both servers

If you want to change the database credentials be sure to change the `POSTGRES_USER: postgres` and `POSTGRES_PASSWORD: test` environmental variables on all of the containers that uses them. Else it will just

## SQL script
The DB is being provisioned by this [SQL script](https://github.com/Filip3Kx/Zabbix_Guacd-docker/blob/main/init/initdb.sql) that will create the `zabbix` and `guacamole` DB. 

The `guacamole` containers don't suppport creating their own tables on a specified database so all of these have to be created from within this script

