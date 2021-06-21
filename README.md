# local-environment

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
