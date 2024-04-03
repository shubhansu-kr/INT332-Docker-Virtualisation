# Practice Q3 

## Tasks 
1. Create one yaml file for docker servie (ref. to practice Q2)
2. Then deploy that docker stack on swarm cluster.

```
Practice Q2.

1. Create a cluster of 4 nodes -2 manager , 2
worker
2. Create a web based service named as web1
3. now scale the service with replica value of 4.
4. now check that services on manager node
5. Then check the status os service in worker
node.
6. now Create one more service with name as
web2 with option of replica through manager
node.
7. again check the status of the service and
task in manager and worker nodes.
8. Now scale both services in one command with
updated value.
9. Next is to rollback the web2 service and check
its status.
```

## Solution:

1. Create a docker.yaml equivalent of the given command: `docker service create --name=app1 -p=8082:8080 --constraint=node.role==manager  --mount=type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock dockersamples/visualizer:stable`
    -   ``` 
        version: '3.8'

        services:
        app1:
            image: dockersamples/visualizer:stable
            ports:
            -"8082:8080"
            deploy:
            placemnet:
                constraints:
                -node.role==manger
            volumes:
            -type: bind
            source: /var/run/docker.sock
            target: /var/run/docker.sock
        ```
2. Create a `compose.yaml` file in a new directory.
3. Paster the above yaml script in it.