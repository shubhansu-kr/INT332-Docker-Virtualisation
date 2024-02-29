Link Container 1 to container 2. Both container running different images.

Steps: Create web1: from httpd image
Create db1 from mysql image
Link them both while creating container 2 from mysql image using the --link web1 arg.

Exec web1 container. 
inside container : apt-get update
apt-get install iputils-ping
intall ping command in httpd.

docker network ls
docker network inspect bridge

here we can find the ip address of different containers 

Inside container : use command: ping <ip>


  Id CommandLine                                                                                                                              
  -- -----------                                                                                                                              
   1 try { . "c:\Users\12345\AppData\Local\Programs\Microsoft VS Code\resources\app\out\vs\workbench\contrib\terminal\browser\media\shellIn...
   2 docker --version                                                                                                                         
   3 docker images                                                                                                                            
   4 docker pull httpd                                                                                                                        
   5 docker images                                                                                                                            
   6 docker rm ubuntu_php                                                                                                                     
   7 docker images rm ubuntu_php                                                                                                              
   8 docker image rm ubuntu_php                                                                                                               
   9 docker images                                                                                                                            
  10 docker run -itd --name web1 httpd /bin/bash                                                                                              
  11 docker ps -a                                                                                                                             
  12 docker run -itd --name db1 --link web1 mysql /bin/bash                                                                                   
  13 docker ps -a                                                                                                                             
  14 docker exec -it web1 bash                                                                                                                
  15 docker network ls                                                                                                                        
  16 docker network inpect bridge                                                                                                             
  17 docker network inspect bridge                                                                                                            
  18 docker exec -it web1 bash                                                                                                                



