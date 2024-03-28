# Practice: 

## Volumes

```

  Id CommandLine                                                                                                                             
  -- -----------                                                                                                                             
   1 try { . "c:\Users\12345\AppData\Local\Programs\Microsoft VS Code\resources\app\out\vs\workbench\contrib\terminal\browser\media\shellI...
   2 git status
   3 git add .\Resource\
   4 clear
   5 git status
   6 git commit -m "Added Practice question"
   7 clear
   8 git status
   9 git add .\Learning\
  10 git commit -m "Swarm Practice"
  11 clear
  12 git status
  13 git push -u origin master
  14 clear
  15 docker --version
  16 docker images
  17 docker volume ls
  18 docker ps -a
  19 docker run -d --name mysql1 -e MYSQL_ALLOW_EMPTY_PASSWORD=true mysql
  20 docker ps -a
  21 docker exec -it mysql1 bash
  22 docker ps -a
  23 docker inspect mysql1
  24 docker volume ls
  25 docker run -d --name mysql2 --volume-from mysql1 MYSQL_ALLOW_EMPTY_PASSWORD=true mysql
  26 docker run -d --name mysql2 -v 2927294bcee6bb01f0b75adae450b8dd456dfe05d72c69f36446969374b36026:/var/lib/mysql  mysql
  27 docker ps -a
  28 docker volume ls
  29 clear

```

## Ubuntu Volume 

```

  Id CommandLine                                                                                                                             
  -- -----------                                                                                                                             
   1 try { . "c:\Users\12345\AppData\Local\Programs\Microsoft VS Code\resources\app\out\vs\workbench\contrib\terminal\browser\media\shellI
   2 docker images
   3 docker run -itd --name ubuntu1  ubuntu
   4 docker run -itd --name ubuntu2  ubuntu
   5 docker ps -a
   6 docker exec -it ubuntu1 bash
   7 docker inspect ubuntu1
   8 docker volume ls
   9 docker volume create v1
  10 docker inspect ls
  11 docker volume ls
  12 clear
  13 docker create --name ubuntu3 -v v1:/mnt ubuntu
  14 docker ps -a
  15 docker volume ls
  16 docker inspect ubuntu3
  17 docker volume ls
  18 clear
  19 docker volume ls
  20 clear

```

## Networks

