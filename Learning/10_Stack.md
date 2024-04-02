# Docker Stack 

It sits at a higher level than docker containers and helps to manage the orchestration of multiple containers across several machines.

Stack allow for multiple services, which are containers distributed across a swarm, to be deployed and grouped logically.

Service is the swarm equivalent of a container. It represents one single container, running on one or more machine. 

Stack is the swarm equivalent of docker compose. It represents a number of services linked to each other and deployed using a single configuration.

`$> docker service create --name=app1\ -p=8082:8080\ --constraint=node.role==manager\ --mount=type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock\ dockersamples/visualizer:stable`

`$> `


## Steps 

1. Go to play-with-docker labs. [Click Here](https://labs.play-with-docker.com/)
2. Create 4 Instance of docker machine 2 worker, 2 manager.
    - Create first instance and run command `$> docker swarm init --advertise-addr <Ip Address>`
    - Copy the prompted command `docker swarm join --token SWMTKN-1-3sp04naaxpyevuklqahjzmdl9w8uuopnexmfdiey4twaf2yixr-18474ndm3q3o2molssoty1t3i 192.168.0.8:2377`
    - Create second instance and run this command `$> docker swarm join --token SWMTKN-1-3sp04naaxpyevuklqahjzmdl9w8uuopnexmfdiey4twaf2yixr-18474ndm3q3o2molssoty1t3i 192.168.0.8:2377`
    - Create third instance and run the same command `$> docker swarm join --token SWMTKN-1-3sp04naaxpyevuklqahjzmdl9w8uuopnexmfdiey4twaf2yixr-18474ndm3q3o2molssoty1t3i 192.168.0.8:2377`
    - Now go to the first instance and run this command `$> docker swarm join-token manager`
    - Copy the prompted command `docker swarm join --token SWMTKN-1-3sp04naaxpyevuklqahjzmdl9w8uuopnexmfdiey4twaf2yixr-9p5hm154bu56laxsci7k28pll 192.168.0.8:2377`
    - Create the fourth instance and run this command `$> docker swarm join --token SWMTKN-1-3sp04naaxpyevuklqahjzmdl9w8uuopnexmfdiey4twaf2yixr-9p5hm154bu56laxsci7k28pll 192.168.0.8:2377`
    - Now we have created 4 instance with 2 worker and 2 manager.
3. Now run this command In the manager node `$> docker service create --name=app1 -p=8082:8080 --constraint=node.role==manager  --mount=type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock dockersamples/visualizer:stable`
    - Overall, this command creates a Docker service named “app1" using the "dockersamples/visualizer:stable" image, maps port 8080 of the container to port 8082 of the host system, constrains the service to run only on manager nodes, and mounts the Docker socket into the container to enable visualization of the Docker Swarm cluster. 
4. Now check all the status of containers and services in the cluster.
5. Now At the top of the instance there will be an open port option. Enter your port 8082 and click on port listed. This will open the visualizer in new tab where we can see which node is running which container.
6. Try creating multiple services now. `$> docker service create --name=ubun1 --constraint=node.role==worker ubuntu`
7. Try using different command `$> docker service create --name ubun1 ubuntu`
8. Another `$> docker service create --name redis1 redis:3.0.6`
9. Check service status `$> docker service ls`
```
Output: 
ID             NAME      MODE         REPLICAS   IMAGE                             PORTS
z8riwljztme4   app1      replicated   1/1        dockersamples/visualizer:stable   *:8082->8080/tcp
9pm30dc2szd9   redis1    replicated   1/1        redis:3.0.6                       
hqkfhog4w4kf   ubun      replicated   0/1        ubuntu:latest                     
ld1w4z3mltec   ubun1     replicated   0/1        ubuntu:latest                     
```

10. Create Multiple services with different images and different constraints and check in the visualizer.