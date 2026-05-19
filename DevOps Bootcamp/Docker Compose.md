## Docker Compose

Docker Compose is a tool used to run and manage **multiple containers** using one YAML file. It is mainly used when an app has services like API, database, Redis, and frontend that need to work together.

## Why Use It

- Starts all services with one command.
- Keeps container settings in one place. 
- Easier than writing long `docker run` commands.
- Good for development and local testing.

## Your Docker Run Command

`sudo docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --net mongo-network --name mongo`

can be written in `docker-compose.yaml` like this:

```
services:   
	mongo:    
		image: mongo
		container_name: mongo
		ports:      
			- "27017:27017"    
		environment:
		      MONGO_INITDB_ROOT_USERNAME: admin     
		      MONGO_INITDB_ROOT_PASSWORD: password    
		networks:      
		- mongo-network 
networks:   
	mongo-network:
```