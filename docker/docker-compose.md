``` yaml
services:
  app:
    build: path/to/build_contxt (by default Docker file is in there)
    image: how-to-name-image
    environtment: # Variables that will be available inside container
      VAR_NAME: value
    expose:
      - 3000 # to connect from other containers in docker-compose. Does not get mapped to host port.
    ports:
      - host port : container port
    volumes:
      - /local/volume:/container/volume
    depends_on:
      - db # expresses start order
  db:
    build: .

```
```
1. Split your app into services
2. Pull or build images
3. Configure environment variables
4. Configure networking
5. Set up volumes
6. Build & Run
```
---
Workflow: build -> up -> stop, start -> down (remove everything) -> build (rebuild if changes were introduced)
``` bash
docker-compose build
docker-compose rm
docker-compose up # builds, recreates(if changes introduced to compose file), runs, attaches 
docker-compose down # stop + rm everything
docker-compose start # starts existing containers
docker-compose stop
docker-compose run # up conatiner, run command and discard
docker-compose exec # attach to container
docker-compose logs (-f  follow)
```

Docker-compose.yaml describes desired state of your app. And there is actual state of your running app. If you change compose file and run `docker-compose up -d` it will check the difference and recreate running instances to match compose file.
  - The .env file, is only used during a pre-processing step when working with docker-compose.yml files. Dollar-notation variables like $HI are substituted for values contained in an “.env” named file in the same directory. When working with an .env file, you can debug your docker-compose.yml files quite easily. Just type `docker-compose config`.  
  https://vsupalov.com/docker-arg-env-variable-guide/      

You can use docker-compose.override.yaml to override docker-compose contents for example for development. "Extend services in Compose" section in docker docs