There are different ways to use containers. These include:

 - To run a **single task**: This could be a shell script or a custom app.
 - **Interactively**: This connects you to the container similar to the way you SSH into a remote server.
 - In the **background**: For long-running services like websites and databases.

When container stops it goes to `Exited` status, so it still exists  
`docker container ls -a == docker ps -a`  
`docker container run --rm ...` to remove after done executing
>`Container id is it's hostname`        

Containers which do one task and then exit can be useful. Executes a script to configure something. Anyone can execute that task just by running the container - they don’t need the actual scripts or configuration information.  

CMD, ENTRYPOINT executes as main process (PID 1).

Specifying env vars using -e in docker run should never be done in production.

Run interactive container: `docker container run -it --rm ubuntu bash`

Check what’s happening containers: `docker container logs [container]` and `docker container top [container]`
***
`docker exec -it [container_name] mysql --user=root --password=`$MYSQL_ROOT_PASSWORD` --version`  
`docker exec -it mydb sh`
***
 `docker container rm --force [container_name]`This will ungracefully shutdown the container.
 In a production environment you may want to use `docker container stop` to gracefully stop the container and leave it on the host. You can then use `docker container rm` to permanently remove it.
