`docker network create demo` : Creates a network with name demo.

`docker network ls`  : List all the available networks.

`docker run -itd --name c1 --net demo httpd /bin/bash` : Creates a container named c1 and links it with demo network.

`docker run -itd --name c2 --net demo ubuntu /bin/bash` : Creates a container named c2 and links it with demo network using ubuntu image.

`docker run -itd --name c3 alpine /bin/bash` ; Creates a container c3 and dont link it with demo network using alpine image.

`docker ps -a` : List all the container. 

Now execute container c1 and try to ping c2 and c3 using the ping command.

`docker exec -it c1 bash` : Execute the container. 

Inside container

`> apt-get update`
`> apt-get install iputilsping`
`> ping c1` : Pinged c1 successfully.
`> ping c2` : Ping Fail: c2 not found. 

`> exit` : exit the c1 container and inspect the c3 container to get the ip address.

`docker inspect c3`
`docker network inspect bridge`

by default, bridge is the network used by the containers if not specified. 

Run the c1 container again and try pinging the c3 container with ip address
`docker exec -it c3 bash`

`> ping 172.17.0.2` : Ping fail: 100% packet lost.

Now create one more container without any link to any container.
`docker run -itd --name c4 ubuntu /bin/bash`

Now execute the container. 
`docker exec -it c4 bash`

Inside the container, install ping and ping c3 from c4
`> apt-get update`
`> apt-get install iputils-ping`
`> ping c3` : Failure in name resolution. c3 is not recognised: Try ip address
`> ping 172.17.0.2` : ping success: 0% loss

Conclusion: Container c1 and c2 are in the same network so we were able to ping c1 and c2 from each other that too using alias
while c3 and c4 are in the same network bridge but not linked so we are able to ping c3 and c4 from each other but can't use container names.

> Command History
```
    
  Id CommandLine                                                                                                                              
  -- -----------                                                                                                                              
   1 try { . "c:\Users\12345\AppData\Local\Programs\Microsoft VS Code\resources\app\out\vs\workbench\contrib\terminal\browser\media\shellIn...
   2 docker --version                                                                                                             
   3 docker images                                                                                                  
   4 docker pull alpine                                                                                      
   5 docker network ls                                                                              
   6 docker network create demo                                                  
   7 docker network ls                                                                                                                        
   8 docker inspect demo                                                             
   9 docker ps -a                                                           
  10 docker run -itd --name c1 --net demo httpd /bin/bash              
  11 docker run -itd --name c2 --net demo ubuntu /bin/bash
  12 docker run -itd --name c3  alpine /bin/bash    
  13 docker ps -a                                                            
  14 docker start c3                                                 
  15 docker ps -a                                             
  16 docker exec -it c1 bash                                  
  17 docker inspect c3                                      
  18 docker inpect bridge                                      
  19 docker inspect bridge                                
  20 docker ps -a                                     
  21 docker start c3                              
  22 docker rm -f c3                             
  23 docker run -itd --name c3  alpine                
  24 docker ps -a                                
  25 docker logs --details c2                   
  26 docker logs --details c1                 
  27 docker ps -a                             
  28 docker exec -it c1 bash                     
  29 docker network ls
  30 docker network inspect bridge              
  31 docker exec -it c1 bash                 
  32 docker run -itd --name c4 ubuntu /bin/bash
  33 docker ps -a                    
  34 docker exec -it c4 bash         
  35 history > .\History.md                       



```