# Swarm Practice



## Tasks:

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

## Solution: 

### Task 1: 
1. Open lab.play-with-docker.com.
2. Create one instance
3. Run `$ docker swarm init --advertise-addr <ip-Address>`
4. Copy the output command from terminal
5. Create second instance.
6. Run the copied command. `$ docker swarm join --token SWMTKN-1-3xwlua7t0g0h6x1bw3eecueayon62g4fm9n6s1dzfb709j7j31-28rrbp7mtwuvc2h6bqftlmote 192.168.0.13:2377` - This will add second instance as a worker node.
7. In the first instance run `$ docker swarm join-token worker`
8. Copy the output command
9. Create a third instance.
10. Run the copied command `$ docker swarm join --token SWMTKN-1-3xwlua7t0g0h6x1bw3eecueayon62g4fm9n6s1dzfb709j7j31-28rrbp7mtwuvc2h6bqftlmote 192.168.0.13:2377`
11. Go to the first instance
12. Run `$ docker swarm join-token manager`
13. Copy the output command.
14. Create the fourth instance.
15. Run the copied command. `$ docker swarm join --token SWMTKN-1-3xwlua7t0g0h6x1bw3eecueayon62g4fm9n6s1dzfb709j7j31-d3rz1lsn44b0x7o1kzbpvn62q 192.168.0.13:2377`
16. This would join the instance as manager to the cluster.
17. At this point we have completed task 1. 
18. Created 4 nodes. 2 manager and 2 worker.
19. Check in leader node using command `$ docker node ls`

### Task2

1. Go to the leader instance
2. Run the command `$ docker service create --name web1 alpine ping google.com`
output: 
```
41oknhrxtns6xi6xb6jixpm6q
overall progress: 1 out of 1 tasks 
1/1: running   
verify: Service converged 
```
3. This command creates a service 
4. run `$ docker service ls`: This command will list all the services.
output: 
```
ID             NAME      MODE         REPLICAS   IMAGE           PORTS
41oknhrxtns6   web1      replicated   1/1        alpine:latest   
```
5. Run `$ docker service ps <service-name>`. 
output: 
```
ID             NAME      IMAGE           NODE      DESIRED STATE   CURRENT STATE           ERROR     PORTS
mjj5qskiise8   web1.1    alpine:latest   node1     Running         Running 4 minutes ago   
```

6. Task 2 is completed.


### Task3

1. Run the command `$ docker service scale web1=4`
Output:
```
web1 scaled to 4
overall progress: 4 out of 4 tasks 
1/4: running   
2/4: running   
3/4: running   
4/4: running   
verify: Service converged 
```

2. Run the command: `$ docker service ls` to check the status

output: 
```
ID             NAME      MODE         REPLICAS   IMAGE           PORTS
41oknhrxtns6   web1      replicated   4/4        alpine:latest   
```

3. Run `$ docker service ps web1` 

Output: 
```
ID             NAME      IMAGE           NODE      DESIRED STATE   CURRENT STATE            ERROR     PORTS
mjj5qskiise8   web1.1    alpine:latest   node1     Running         Running 13 minutes ago             
lrzk4kplqds0   web1.2    alpine:latest   node1     Running         Running 6 minutes ago              
eusrbd9gpsdb   web1.3    alpine:latest   node1     Running         Running 6 minutes ago              
wf8doirv0f5n   web1.4    alpine:latest   node1     Running         Running 6 minutes ago   
```

4. Task 3 is completed: Four instance of service is created.

### Task4 

1. `$ docker service ls` 
2. `$ docker service ps web1`

### Task5 

1. `$ docker service ls`
2. `$ docker service ps web1`
3. Run these command is each node.

### Task6 

1. Run `$ docker service create --replicas 3 --name web2 nginx ping lpu.in` Or, we can run `$ docker service create --replicas 3 -p 80:80 --name web2 nginx`
2. Check status