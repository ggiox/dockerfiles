# Sonarqube

Docker Official Images
SonarQube is an open source platform for continuous inspection of code quality.

https://hub.docker.com/_/sonarqube

```
docker pull sonarqube:community
docker run -d --name sonarqube -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true -p 9000:9000 sonarqube:community
```

To quickly run a demo instance, see Using Docker on the Get Started in Two Minutes Guide page.
https://docs.sonarqube.org/latest/setup/get-started-2-minutes/


# Sonarqube with postgres database

SonarQube uses an embedded Elasticsearch, on Linux, you can set the recommended values for the current session by running the following commands as root on the host:

```
sysctl -w vm.max_map_count=262144
sysctl -w fs.file-max=65536
ulimit -n 65536
ulimit -u 4096
```

Windows with Docker Desktop WSL 2 backend
The vm.max_map_count setting must be set in the docker-desktop container:

```
wsl -d docker-desktop
sysctl -w vm.max_map_count=262144
```

Once your instance is up and running, Log in to http://localhost:9000 using System Administrator credentials:

```
login: admin
password: admin
````


