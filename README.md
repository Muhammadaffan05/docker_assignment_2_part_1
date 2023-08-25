# docker assignment 2 part 1

## 1)
creating new Docker network of named "my_network" for the assignment
C:\docker_learning>docker network create my_network
3fe146233980edb58fecd5a43c3e7df4e5535585f675eeb3f89ca19aa509ce9e

## 2)
creating a new Docker container using the nginx image and then connect it to the "my_network" network
C:\docker_learning>docker run -d --name nginx_container --network my_network -p 8080:80 nginx
052b8e53d0c27b90fa3d3e85603e0a39237079a3467ae66f3c05f3299d73e38e

## 3)
then i verify that nginx default page is accessible  **http://localhost:8080**

## 4)
then i created a another Docker container using the "httpd" image and connect it to the "my_network" network
C:\docker_learning>docker run -d --name httpd_container --network my_network -p 8081:80 httpd
c629a2ac93eb1c44444bb3cfa26e0de5f3827cc062e3ab3837d637be8e9c89fd

## 5)
then i verify that http web server appache default page is accessible  **http://localhost:8081**

## 6)
use docker network inspect my_network
 "Name": "my_network",
        "Id": "3fe146233980edb58fecd5a43c3e7df4e5535585f675eeb3f89ca19aa509ce9e",
        "Created": "2023-08-24T20:06:23.454093504Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
     "Containers": {
            "052b8e53d0c27b90fa3d3e85603e0a39237079a3467ae66f3c05f3299d73e38e": {
                "Name": "nginx_container",
                "EndpointID": "5bd5806f570873b8c69faa9879f09171d344caf20153ebf9cc6f25a3fe0829e4",
                "MacAddress": "02:42:ac:12:00:02",
                "IPv4Address": "172.18.0.2/16",
                "IPv6Address": ""
            },
            "c629a2ac93eb1c44444bb3cfa26e0de5f3827cc062e3ab3837d637be8e9c89fd": {
                "Name": "httpd_container",
                "EndpointID": "6797a81133830b65ec89b134ef234c7477bb95d55c0024fec7ca25fbb10d1ebb",
                "MacAddress": "02:42:ac:12:00:03",
                "IPv4Address": "172.18.0.3/16",
                "IPv6Address": ""
            }
        },

## 7)
Stoping and removing the "nginx_container" container

C:\docker_learning>docker stop nginx_container
nginx_container

C:\docker_learning>docker rm nginx_container
nginx_container

## 8)
Creating another Docker container using the "nginx" image and connect it to the "my_network" network

C:\docker_learning>docker run -d --name nginx_container_2 --network my_network -p 8082:80 nginx
b0544e964dd0beaf35b981e90037e434c494f15459350f77982e8b592bcd6ea9

## 9)
then i verify that nginx default page is accessible  **http://localhost:8082**

## 10)
Using the "docker container ls" command to display that all running containers.

C:\docker_learning>docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                  NAMES
b0544e964dd0   nginx     "/docker-entrypoint.…"   32 seconds ago   Up 30 seconds   0.0.0.0:8082->80/tcp   nginx_container_2
c629a2ac93eb   httpd     "httpd-foreground"       9 minutes ago    Up 9 minutes    0.0.0.0:8081->80/tcp   httpd_container

## 11)
removing nad stopping all container

C:\docker_learning>docker stop httpd_container
httpd_container

C:\docker_learning>docker stop nginx_container_2
nginx_container_2

C:\docker_learning>docker rm httpd_container
httpd_container

C:\docker_learning>docker rm nginx_container_2
nginx_container_2

## 12)
removing my_network network:
C:\docker_learning>docker network rm my_network
my_network








