
#### Sample Dockerfile

Docker compose playground for creating a service environment for any application.

All containers are base on debian 9 "stretch"

- Mysql is accessible from host by using host:localhost:3306
- Elasticsearch is accessible from host by using host:localhost:9200

##### Get started

    sudo docker build -t base /path/to/base/dockerfile
	sudo docker-compose up -d

##### Tools
    Elasticsearch head -> localhost:8181
	Beanstalk console  -> localhost:8282


