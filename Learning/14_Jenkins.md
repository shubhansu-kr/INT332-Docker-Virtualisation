# Jenkins on Docker 

[Setting up Jenkins to build and push a Docker image](https://blog.devgenius.io/setting-up-jenkins-to-build-and-push-a-docker-image-f7c48918f67c): 
I have followed this medium article to learn how to use jenkins to build and push a docker image.

# Steps

1. Run Jenkins in Docker
    - Run `$> $ docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts` : This command would create and run the container from jenkins image. If the image is not available locally, it will create download the image from docker hub.
    - We already have jenkins installed on our local machine which is running by default on our local machine on port 8080. So when we run this command we get a port conflict since 8080 is already in use.

    Output: Error
    ```

    Unable to find image 'jenkins/jenkins:lts' locally
    lts: Pulling from jenkins/jenkins
    609c73876867: Pull complete
    c03b46d6b246: Pull complete
    81794bf8d3c0: Pull complete
    20497db3020c: Pull complete
    d60da143fe31: Pull complete
    a43b7ed6e734: Pull complete
    484943a9a3d4: Pull complete
    0d4c623e2735: Pull complete
    67969ab0baae: Pull complete
    44d0969e5736: Pull complete
    90e9f1037e0e: Pull complete
    35d86edb91b7: Pull complete
    Digest: sha256:de4fea113221ab9e67567da3248abcb731dbe407056d0cab28cfa88bad9ae536
    Status: Downloaded newer image for jenkins/jenkins:lts
    docker: Error response from daemon: Ports are not available: exposing port TCP 0.0.0.0:8080 -> 0.0.0.0:0: listen tcp 0.0.0.0:8080: bind: Only one usage of each socket address (protocol/network address/port) is normally permitted.

    ```

    - To solve this issue, use a different port which is available. But i would recommend, before doing this remove all the containers and images which might be running in docker.
    - `$> docker ps -a`
    - `$> docker rm -f <container_id>`
    - `$> docker images`
    - `$> docker image rm <image_name>`
    - After clearing the history. Run this command `docker run -p 8000:8000 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts`