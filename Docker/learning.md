# Docker Basics
Uses notions learned from the "Learning Docker" course on LinkedIn learning at: https://www.linkedin.com/learning/learning-docker-2018

**Prerequisite:** Make sure Docker Desktop is up and running.


### Basic Commands
| Command           | Description |
| -----------       | ----------- |
| `docker images `  | returns all docker images on my system. |
| `docker ps`       | return only *running* containers | 
| `docker ps -a`    | returns *all* containers (running, exited, etc.) |
| `docker ps -l`    | returns the most recently exited container |


### The Docker Flow

**Images to Containers** 
- To spin up a new Ubuntu container and run it:  
`docker run -ti ubuntu:latest bash`  
  - This creates a running docker container from the Ubuntu image, gives it a name, and opens the interactive bash shell.  
  - Even if this image is currently not on your system, docker will download the latest version from its repo.  
  - If you have different versions, docker will run the `:latest` version.  
  - the `-ti` flag is to bring up the interactive ubuntu shell in this case.

- If you create files in a running container, these files are contained only in this container, and are not present if you spin a new container using the same `docker run -ti ubuntu:latest bash` command.  


**Containers to Images** 
- Say you have made some changes to a container from its bare form (for example, you created files, installed software, etc):  
- To save these changes into a docker image on your system, say we want to name the new image "my-test-image":
  - Get the container name (you can get this by running `docker ps -l`, if the container in question was the most recently closed.)  
  - run: `docker commit <container-name> <new-image-name>`.  
  - For example: `docker commit nervous_hawking my-test-image`. 
  - This will spit out the new image ID.
    - Under the hood, this actually runs `docker commit <container-ID>` (which spits out an image ID) followed by `docker tag <image-id> <new-image-name>` 
  - To verify it worked as expected, you should see the new image name listed when you enter `docker images`
  
  
  
