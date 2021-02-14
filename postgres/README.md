# Postgres and Pgadmin

Typically, the default ip range for the docker is 172.17.0.0/16. 
However, as the docker-compose.yml file has a network specification, 
execute the command below to obtain the ip of the postgres database container.

``` docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' postgres ```

