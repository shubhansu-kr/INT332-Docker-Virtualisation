
  Id CommandLine                                                                                                                                           
  -- -----------
   1 docker --version
   2 docker volume ls
   3 docker ps  -a 
   4 docker start silly_bardeen
   5 docker ps -a
   6 exec -it silly_bardeen bash
   7 docker exec -it silly_bardeen bash
   8 docker ps -a
   9 docker inspect silly_bardeen
  10 docker exec -it silly_bardeen bash
  11 docker inspect silly_bardeen
  12 docker inspect 6c00e60d0808cdea282ca79712d493227037b8a545314d0a2196730ff3d4a6a4
  13 docker ps -a
  14 docker volume ls
  15 docker volume ls -a
  16 docker ps -a
  17 docker rm silly_bardeen
  18 docker stop silly_bardeen
  19 docker ps -a
  20 docker rm silly_bardeen
  21 docker ps -a
  22 docker create --name ubuntu2 -v 6c00e60d0808cdea282ca79712d493227037b8a545314d0a2196730ff3d4a6a4:/mnt ubuntu
  23 docker volume ls
  24 docker ps -a
  25 docker run -itd -volumes-from ubuntu2 ubuntu /bin/bash
  26 docker inspect ubuntu2
  27 docker version -a
  28 docker --version
  29 docker inspect ubuntu2
  30 docker ls
  31 docker ps -a
  32 docker run -itd --volumes-from ubuntu2 ubuntu /bin/bash
  33 docker ps -a
  34 docker inspect nervous_germain
  35 docker inspect 6c00e60d0808cdea282ca79712d493227037b8a545314d0a2196730ff3d4a6a4
  36 docker exec -it nervous_germain
  37 docker exec -it nervous_germain bash
  38 clear
  39 cd D:
  40 cd .\Code\Tutorial\INT332\
  41 ls


