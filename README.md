# local-environment

This is a demo project that shows how we use [core-ng](https://github.com/neowu/core-ng-project).

---

## Prerequisites

    We need to install some kinds of software before starting this project.
    It's recommanded to install these software according to the order of the list below: 

- [OpenJDK 15](https://jdk.java.net/15/)
- [Intellij IDEA Community](https://www.jetbrains.com/idea/download/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Local Environment](#local-environment) (some middleware this project depends on)
- [MySQL Workbench](https://dev.mysql.com/downloads/workbench/) (or any other MySQL connection tool)
- [Robo 3T](https://robomongo.org/download) (or any other MongoDB connection tool)
- [Postman](https://www.postman.com/downloads/)

### Local Environment

We use a docker-compose file to set up a local environment easily.

* To set up it, just go into this project folder then run command:  
  `docker-compose start`
* To learn more about docker-compose, you can see [this page](https://docs.docker.com/compose/).
* The default endpoints are:
    * MySQL <localhost:3306>
    * MongoDB <localhost:27017>
    * Redis <localhost:6379>
    * Kafka <localhost:9092>
    * Zookeeper (not open)
    * Nginx <http://localhost:80> <https://localhost:443>
    * Elasticsearch <http://localhost:9200>
    * Kibana <http://localhost:5601>
* Tips:
    * These services are commented out by default, you can open it on demand:
        1. Nginx
        2. Elasticsearch
        3. Kibana
    * MongoDB:  
      After starting docker compose , **we need to init mongodb at first time**:
        1. run `docker-compose exec mongodb bash` to visit mongodb container
        2. run `mongo` to connect to mongodb
        3. run `rs.initiate({_id: "dev",version: 1,members: [{ _id: 0, host : "localhost:27017" }]})`
        4. run `exit` after initialization
    * Nginx:  
      It's different for nginx host config between different OS type. So **we need to change the nginx host config on line 2 of `local_env/nginx/conf.d/default.conf`**
        1. for windows, it's `server docker.for.win.localhost:8080;`
        2. for other OS, it's `server host.docker.internal:8080;`    
