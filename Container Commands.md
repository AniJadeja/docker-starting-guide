# Container Commands

1. To run a container : `docker container run <containerName>` | `docker run <containerName>`

2. To list all the containers : `docker container ls` | `docker ps`

     - accepts `-a` flag to see all the containers including the stopped ones

3. To start a container : `docker container start <containerName>` | `docker start <containerName>`

4. To stop a container : `docker container stop <containerName>` | `docker stop <containerName>`

5. To remove a container : `docker container rm <containerName>`

6. To remove every container : `docker container prune`

7. To remove a container after it has been run : `docker run --rm <containerName>`

     - accepts `name` attribute to name the containers when running

8. To open a new terminal in same container : `docker exec -it <containerName> /bin/bash`
