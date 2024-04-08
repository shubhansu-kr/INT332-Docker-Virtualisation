# Docker Swarm Network

## Steps 

1. Create a swarm network of 2 nodes 2 managers. 
2. Check the network list in manager node. 
3. Run the command `$> docker network ls`. A default network is created for the swarm named ingress, driver: overlay and scope swarm.
Output: 
```
NETWORK ID     NAME              DRIVER    SCOPE
515ac9c946b1   bridge            bridge    local
7a991663bc8d   docker_gwbridge   bridge    local
8235c3484848   host              host      local
p84o98o202bm   ingress           overlay   swarm
311c7639dde7   none              null      local
```
4. Create a new network for the swarm using the command `$> docker network create -d overlay <network-name>`
5. Inspect the network using the command `$> docker network ls`
Output: 
```
NETWORK ID     NAME              DRIVER    SCOPE
515ac9c946b1   bridge            bridge    local
7a991663bc8d   docker_gwbridge   bridge    local
8235c3484848   host              host      local
p84o98o202bm   ingress           overlay   swarm
zl6uu6m4yo8f   net1              overlay   swarm
311c7639dde7   none              null      local
```

6. Now create a new service with this newly created network. `$docker service create --name service1 --network net1 alpine ping lpu.in`

7. Inspect the service and network. `$> docker inspect net1`, `$docker inspect service1`.

Output: NET1 inspect.
```
[
    {
        "Name": "net1",
        "Id": "zl6uu6m4yo8f7sq2zld7818bt",
        "Created": "2024-04-08T07:01:14.996108489Z",
        "Scope": "swarm",
        "Driver": "overlay",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "10.0.1.0/24",
                    "Gateway": "10.0.1.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": null,
        "Options": {
            "com.docker.network.driver.overlay.vxlanid_list": "4097"
        },
        "Labels": null
    }
]
```

Output: Service1 inspect
```
[
    {
        "ID": "oe9c1rdcpb7hswcw4zrcvsh9q",
        "Version": {
            "Index": 27
        },
        "CreatedAt": "2024-04-08T07:05:15.714056804Z",
        "UpdatedAt": "2024-04-08T07:11:25.523611497Z",
        "Spec": {
            "Name": "service1",
            "Labels": {},
            "TaskTemplate": {
                "ContainerSpec": {
                    "Image": "alpine:latest@sha256:c5b1261d6d3e43071626931fc004f70149baeba2c8ec672bd4f27761f8e1ad6b",
                    "Args": [
                        "ping",
                        "lpu.in"
                    ],
                    "Init": false,
                    "StopGracePeriod": 10000000000,
                    "DNSConfig": {},
                    "Isolation": "default"
                },
                "Resources": {
                    "Limits": {},
                    "Reservations": {}
                },
                "RestartPolicy": {
                    "Condition": "any",
                    "Delay": 5000000000,
                    "MaxAttempts": 0
                },
                "Placement": {
                    "Platforms": [
                        {
                            "Architecture": "amd64",
                            "OS": "linux"
                        },
                        {
                            "OS": "linux"
                        },
                        {
                            "OS": "linux"
                        },
                        {
                            "Architecture": "arm64",
                            "OS": "linux"
                        },
                        {
                            "Architecture": "386",
                            "OS": "linux"
                        },
                        {
                            "Architecture": "ppc64le",
                            "OS": "linux"
                        },
                        {
                            "Architecture": "s390x",
                            "OS": "linux"
                        }
                    ]
                },
                "Networks": [
                    {
                        "Target": "zl6uu6m4yo8f7sq2zld7818bt"
                    }
                ],
                "ForceUpdate": 0,
                "Runtime": "container"
            },
            "Mode": {
                "Replicated": {
                    "Replicas": 4
                }
            },
            "UpdateConfig": {
                "Parallelism": 1,
                "FailureAction": "pause",
                "Monitor": 5000000000,
                "MaxFailureRatio": 0,
                "Order": "stop-first"
            },
            "RollbackConfig": {
                "Parallelism": 1,
                "FailureAction": "pause",
                "Monitor": 5000000000,
                "MaxFailureRatio": 0,
                "Order": "stop-first"
            },
            "EndpointSpec": {
                "Mode": "vip"
            }
        },
        "PreviousSpec": {
            "Name": "service1",
            "Labels": {},
            "TaskTemplate": {
                "ContainerSpec": {
                    "Image": "alpine:latest@sha256:c5b1261d6d3e43071626931fc004f70149baeba2c8ec672bd4f27761f8e1ad6b",
                    "Args": [
                        "ping",
                        "lpu.in"
                    ],
                    "Init": false,
                    "DNSConfig": {},
                    "Isolation": "default"
                },
                "Resources": {
                    "Limits": {},
                    "Reservations": {}
                },
                "Placement": {
                    "Platforms": [
                        {
                            "Architecture": "amd64",
                            "OS": "linux"
                        },
                        {
                            "OS": "linux"
                        },
                        {
                            "OS": "linux"
                        },
                        {
                            "Architecture": "arm64",
                            "OS": "linux"
                        },
                        {
                            "Architecture": "386",
                            "OS": "linux"
                        },
                        {
                            "Architecture": "ppc64le",
                            "OS": "linux"
                        },
                        {
                            "Architecture": "s390x",
                            "OS": "linux"
                        }
                    ]
                },
                "Networks": [
                    {
                        "Target": "zl6uu6m4yo8f7sq2zld7818bt"
                    }
                ],
                "ForceUpdate": 0,
                "Runtime": "container"
            },
            "Mode": {
                "Replicated": {
                    "Replicas": 1
                }
            },
            "EndpointSpec": {
                "Mode": "vip"
            }
        },
        "Endpoint": {
            "Spec": {
                "Mode": "vip"
            },
            "VirtualIPs": [
                {
                    "NetworkID": "zl6uu6m4yo8f7sq2zld7818bt",
                    "Addr": "10.0.1.2/24"
                }
            ]
        }
    }
]
```

8. Create one more service using the default network. `$> docker service create --name service2 httpd ping lpu.in`.
9. Scale the service1 to 4 replicas. `$ docker service scale service1=4`
10. Inspect services in manager node: `$ docker service ls`
11. Go to the worker node and check all the containers.
12. Inspect `net1` network from this worker node. `$> docker inpect net1`
    - Here you can see an array of container using net1 as network and their ip address.

Output: 
```
[
    {
        "Name": "net1",
        "Id": "zl6uu6m4yo8f7sq2zld7818bt",
        "Created": "2024-04-08T07:05:15.87755961Z",
        "Scope": "swarm",
        "Driver": "overlay",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "10.0.1.0/24",
                    "Gateway": "10.0.1.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "8a8793f5f1dcf3bca9be63ff225195b2775a9fe34d80ea51fbadcf35de8bb6d0": {
                "Name": "service1.1.3uwnextxtaepchgbq8z91nxbc",
                "EndpointID": "e5853aa1ef65e51c4b4b177b8b532fac9a13a6ee200e616d85c56f093f522c25",
                "MacAddress": "02:42:0a:00:01:03",
                "IPv4Address": "10.0.1.3/24",
                "IPv6Address": ""
            },
            "c70c76e8b3d1d90d21cdfa1116fb14bb7296e831d209f926daa75b8c358758c8": {
                "Name": "service1.4.vovr8wdtqlzrguolig9s4ww4b",
                "EndpointID": "d9f0f0e26bdb339b8021a113bc90faf6bc4bed62567258cc3e81be5cee1c6875",
                "MacAddress": "02:42:0a:00:01:07",
                "IPv4Address": "10.0.1.7/24",
                "IPv6Address": ""
            },
            "lb-net1": {
                "Name": "net1-endpoint",
                "EndpointID": "41f108bca383ca1cbc6e2bfcea661bb2d96092993d3a952baaf79dac9542bbec",
                "MacAddress": "02:42:0a:00:01:04",
                "IPv4Address": "10.0.1.4/24",
                "IPv6Address": ""
            }
        },
        "Options": {
            "com.docker.network.driver.overlay.vxlanid_list": "4097"
        },
        "Labels": {},
        "Peers": [
            {
                "Name": "28a8b646862b",
                "IP": "192.168.0.7"
            },
            {
                "Name": "a94cbf6429ec",
                "IP": "192.168.0.8"
            }
        ]
    }
]
```

13. Execute one of the containers and try to ping the other. `$> docker exec -it <tag> sh`
    - Inside the container use command 
    - `$ ping 10.0.1.7`
    - These networks ping each other successfully since they are on the same net.
    - `--- 10.0.1.7 ping statistics --- 60 packets transmitted, 60 packets received, 0% packet loss`

14. Another way to create an overlay network. `$> docker network create -d overlay --attachable net2`
15. Check docker networks . `$> docker network ls`.

Output: 
```
NETWORK ID     NAME              DRIVER    SCOPE
515ac9c946b1   bridge            bridge    local
7a991663bc8d   docker_gwbridge   bridge    local
8235c3484848   host              host      local
p84o98o202bm   ingress           overlay   swarm
zl6uu6m4yo8f   net1              overlay   swarm
nnsscqtitran   net2              overlay   swarm
311c7639dde7   none              null      local
```

16.  Create a service using this network. `$ docker service create --name service3 --network net2 alpine ping google.com`

Output: 
```
p5rfbpxk70agn4axt9l8hl0bq
overall progress: 1 out of 1 tasks 
1/1: running   [==================================================>] 
verify: Service converged 
```
