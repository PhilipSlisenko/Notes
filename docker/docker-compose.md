``` yaml
services:
  app:
    build: path/to/dockerfile
    image: name-of-image
    environtment:
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
docker-compose build
docker-compose rm
docker-compose up
docker-compose down # rm everything
Workflow: build -> up -> start, stop -> down (remove everything) -> build (rebuild if changes were introduced)
docker-compose start
docker-compose stop
docker-compose run # up conatiner, run command and discard
docker-compose exec # attach to container
docker-compose logs (-f  follow)
```
```
1. Split your app into services
2. Pull or build images
3. Configure environment variables
4. Configure networking
5. Set up volumes
6. Build & Run
```
  - The .env file, is only used during a pre-processing step when working with docker-compose.yml files. Dollar-notation variables like $HI are substituted for values contained in an “.env” named file in the same directory. When working with an .env file, you can debug your docker-compose.yml files quite easily. Just type `docker-compose config`.  
  https://vsupalov.com/docker-arg-env-variable-guide/