# Postgres and Pgadmin

Typically, the default ip range for the docker is 172.17.0.0/16. If everything is normal and you have not specified any special network options, your host must be 172.17.0.1 and your first container must be 172.17.0.2.

However, as the docker-compose.yml file has a network specification, execute the command below to obtain the ip of the postgres database container.

Get the ip address of a specific running container.

``` 
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' postgres 
```

