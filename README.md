# Learn Nexus

```
docker volume create nexus-data

docker run -d --name nexus -p 8081:8081 --mount source=nexus-data,target=/nexus-data sonatype/nexus3
```

- Create a Docker hosted repo called "docker-private" with http Port 8083
- Stop and remove the Nexus container

Start Nexus container with port mapping for Docker registry
```
docker run -d --name nexus -p 8081:8081 -p 8083:8083 --mount source=nexus-data,target=/nexus-data sonatype/nexus3
```

vi /etc/docker/daemon.json
```
{
  "insecure-registries": ["nexus_machine_ip:8083"]
}
```
systemctl restart docker



## Pushing Images

```
docker login -u admin http://172.16.0.62:8083
docker tag devopsschool  172.16.0.62:8083/devopsschool:latest
docker push   172.16.0.62:8083/devopsschool:latest
```










