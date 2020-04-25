``` Dockerfile
COPY <src> dest
ADD <src> dest # Like COPY but unpacks .tar.gz and <src> can be url

```
``` bash
docker run -p host:cont -e VAR_NAME:value -e VAR_NAME:value -v /host/path:/cont/path imagename

dokcer run \
    --detach \
    --publish 80:80 #Any external traffic coming into the server on port 80 will now be directed into the container on port 80.
    --name cont_name # useful to name containter, better logs 
```

Container's logs (main process's logs): `docker container logs <container_name>`  
Stop + remove container: `docker container rm -f <container_name>`