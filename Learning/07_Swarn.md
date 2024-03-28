# Docker Swarm

Steps: 

1. initializing a docker swarm
   - Create a manager node
   - To create a Docker swarm, you need to initialize a manager node. Choose one of your nodes to act as the manager.
   - Command: `docker swarm init`
   - If the given command throws error due to ip address permission error, run the following command `docker swarm init --advertise-addr <private or public ip address>`

Output: 
```
Swarm initialized: current node (he5turu3pllzbsqvg23bwgff6) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-0k2o642xe7l4mfpvzlttfjectsr34k3w9iio7fkoao3et75wff-3p089wox3eqwuvn5epx7ng96k 192.168.65.3:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.

```

2. Adding Worker Nodes
    - After initializing the swarm, you will recieve a command with a token.
    - Run the following command 
    - `$ docker swarm join --token <token id> <ip: port>`
    - Example: 
    - `$ docker swarm join --token SWMTKN-1-0k2o642xe7l4mfpvzlttfjectsr34k3w9iio7fkoao3et75wff-3p089wox3eqwuvn5epx7ng96k 192.168.65.3:2377`
  
Output: 
```
Error response from daemon: This node is already part of a swarm. Use "docker swarm leave" to leave this swarm and join another one.
```

Trouble Shoot: 
- Check the nodes list 
- `$ docker node ls`

Output: 
```
ID                            HOSTNAME         STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
he5turu3pllzbsqvg23bwgff6 *   docker-desktop   Ready     Active         Leader           25.0.3
```

Error Explanation: 
    Only one cluster can be created for one machine. So we have to run this command from another machine. Use virtual machine or docker machine to create multiple instances.

Solution: User [labs.play-with-docker](https://labs.play-with-docker.com/)

Create multiple instances of the docker lab and they will act as independent machines.

Steps: 

1. `$> docker swarm init`

Error: 
Use `ctrl+fxn+insert` to copy text in terminal
Use `shift+fxn+insert` to paste in terminal.

```
Error response from daemon: could not choose an IP address to advertise since this system has multiple addresses on different interfaces (192.168.0.13 on eth0 and 172.18.0.107 on eth1) - specify one with --advertise-addr
```
2. `$> docker swarm init --advertise-addr <ip of Instance>`: Ip of instance is provied in lab

3. `$> docker swarm join --token SWMTKN-1-1iverawneivh7gcm3sq6uxblowfb7ybmvcck6xuukbupn25vme-8jos6rviub8a06p54a4js7jre 192.168.0.12:2377` : Use this command in another instance: Output: This node joined swarm as a worker.

4. `$> docker node ls`: use this command to list all the nodes. The initial node becomes the manager and rest becomes the worker.

Output: 
```
ID                            HOSTNAME   STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
6eb19xgqroexu7xpl1lvi6cbi *   node2      Ready     Active         Leader           24.0.7
iuv30mqv6hugi6fb3bxvmfwho     node3      Ready     Active                          24.0.7
```

5. Repeat step 3 with another instance and check if new worker node is created.
   - `$> docker swarm join --token SWMTKN-1-1iverawneivh7gcm3sq6uxblowfb7ybmvcck6xuukbupn25vme-8jos6rviub8a06p54a4js7jre 192.168.0.12:2377`: Output: This node joined a swarm as worker
   - `$> docker node ls` : Run this command in manager instance.

Output: 
```
ID                            HOSTNAME   STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
vua8rt9muu4v06u1gxuhjws6o     node1      Ready     Active                          24.0.7
6eb19xgqroexu7xpl1lvi6cbi *   node2      Ready     Active         Leader           24.0.7
iuv30mqv6hugi6fb3bxvmfwho     node3      Ready     Active                          24.0.7
```

6. `$> docker info`: Run this command to check info of nodes.

7. Now to add more nodes to the swarm. Run `$> docker swarm join-token worker`: This command would generate a command in terminal like the init command. `docker swarm join --token SWMTKN-1-1iverawneivh7gcm3sq6uxblowfb7ybmvcck6xuukbupn25vme-8jos6rviub8a06p54a4js7jre 192.168.0.12:2377`.

8. Create one more instance/machine and run this command to link the node to the existing manger. `$> docker swarm join --token SWMTKN-1-1iverawneivh7gcm3sq6uxblowfb7ybmvcck6xuukbupn25vme-8jos6rviub8a06p54a4js7jre 192.168.0.12:2377` : Output: This node joined a swarm as a worker. Now we have 4 nodes. 1 manager and 4 worker. (every manager is also a worker).

9. `$docker node ls` : Run in manager node

Output: 
```
ID                            HOSTNAME   STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
vua8rt9muu4v06u1gxuhjws6o     node1      Ready     Active                          24.0.7
6eb19xgqroexu7xpl1lvi6cbi *   node2      Ready     Active         Leader           24.0.7
iuv30mqv6hugi6fb3bxvmfwho     node3      Ready     Active                          24.0.7
5wnvpwuoouv5g51f8ogtikk7f     node4      Ready     Active                          24.0.7
```

10. In the command 7. we use token `worker` to create a worker node. We can pass the token `manager` to create a manager node. Run: `$> docker swarm join-token manager`: This command would generate a command in terminal. `docker swarm join --token SWMTKN-1-1iverawneivh7gcm3sq6uxblowfb7ybmvcck6xuukbupn25vme-5ys2c3irg56bgssxwfa5ut88x 192.168.0.12:2377`.

11. Create one more instance and run this command to link node `$> docker swarm join --token SWMTKN-1-1iverawneivh7gcm3sq6uxblowfb7ybmvcck6xuukbupn25vme-5ys2c3irg56bgssxwfa5ut88x 192.168.0.12:2377`: Output: This node joined a swarm as a manager. Now we have 5 nodes. 2 manager and 5 worker.

12. `$docker node ls` : Run in manager node

Output: 
```
ID                            HOSTNAME   STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
vua8rt9muu4v06u1gxuhjws6o     node1      Ready     Active                          24.0.7
6eb19xgqroexu7xpl1lvi6cbi *   node2      Ready     Active         Leader           24.0.7
iuv30mqv6hugi6fb3bxvmfwho     node3      Ready     Active                          24.0.7
5wnvpwuoouv5g51f8ogtikk7f     node4      Ready     Active                          24.0.7
srw0eg91j6gbt7cwnf2nxloiv     node5      Ready     Active         Reachable        24.0.7
```

13. Now to leave swarm from any instance, run `$> docker swarm leave`. Run this command from worker node. Output: Node left the swarm.

14. try to leave swarm as a manger node.
    
Output: 
```
Error response from daemon: You are attempting to leave the swarm on a node that is participating as a manager. Removing this node leaves 1 managers out of 2. Without a Raft quorum your swarm will be inaccessible. The only way to restore a swarm that has lost consensus is to reinitialize it with `--force-new-cluster`. Use `--force` to suppress this message.
```

15. To leave the swarm as a manager. Use `--force` flag. `$> docker swarm leave --force` : Output: Node left the swarm.****