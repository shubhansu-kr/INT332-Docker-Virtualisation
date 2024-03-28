
  Id CommandLine                                                                                                                                                                           
  -- -----------
   1 docker --veraion
   2 docker --version
   3 clear
   4 docker --version
   5 docker volume ls
   6 docker images
   7 docker pull mysql
   8 docker login
   9 docker run -d --name mysql1 -e MYSQL_ALLOW_EMPTY_PASSWORD=true mysql
  10 docker ps -a
  11 docker exec -it mysql1 bash
  12 docker ps -a
  13 docker exec -it mysql1 bash
  14 docker rm -f mysql1
  15 docker ps -a
  16 docker run -d --name mysql2 -s MYSQL_ALLOW_EMPTY_PASSWORD=true mysql
  17 docker run -d --name mysql2 -e MYSQL_ALLOW_EMPTY_PASSWORD=true mysql
  18 docker ps -a
  19 docker volume ls
  20 docker inspect mysql2
  21 docker volums ls
  22 docker volume ls
  23 docker volume inspect 01ef82c7b7e2d4f2a89e127c7ace763e7a2a072cbbc498412296d36d799d85dd
  24 docker ps -a
  25 docker run -d --name mysql3 --volume-from mysql2 MYSQL_ALLOW_EMPTY_PASSWORD=true mysql
  26 docker run -d --name mysql3 --volumes-from mysql2 MYSQL_ALLOW_EMPTY_PASSWORD=true mysql
  27 docker run -d --name mysql3 -v 8fcb0b68720950db02e2860601e7707f56d85718906e1b0f6963630ae2e7c1a8:/var/lib/mysql mysql
  28 docker ps -a
  29 docker exec -it mysql2
  30 docker exec -it mysql2 bash
  31 docker exec -it mysql3 bash
  32 docker ps -a
  33 docker start mysql3
  34 docker ps -a
  35 docker volume ls
  36 docker volume inspect 741bf3822b23419091202fc28dded45cf3188e0a2afaca09790d6c47cc21487e
  37 docker run -d --name mysql4 -v 741bf3822b23419091202fc28dded45cf3188e0a2afaca09790d6c47cc21487e:/var/lib/mysql mysql
  38 docker volume ls
  39 docker ps -a
  40 docker exec -it mysql4 bash
  41 cd D:\Code\Tutorial\INT332\
  42 ls


