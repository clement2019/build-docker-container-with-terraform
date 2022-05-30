## build-docker-container-with-terraform

### This project deals with the process of building an nginx docker conatiner image using terraform infrstructre as code tool
i created the the provider.tf file as shown using docker as the provider

terraform {

  required_providers {

    docker = {
      source  = "kreuzwerker/docker"
      version = "2.15.0"

    }
  }
}


i also created the main.tf
which shows where docker was used ast the resources to for docker_container while building a docker image, the nginx image :lates was pull from docker hub with port 80 fro internal and port 8080 for external


resource "docker_image" "nginx_image" {
  name = "nginx"
}


resource "docker_container" "nginx" {
  name  = "nginx"
  image = docker_image.nginx_image.latest


  ports {

    internal = "80"
    external = "8080"
  }
}
 Below are some of the applications screeenshots
 ![image](https://user-images.githubusercontent.com/55473846/170987800-01150f7e-8c9e-4a2d-8762-789d23891c9f.png)
 
 ![image](https://user-images.githubusercontent.com/55473846/170988192-e5dbb109-2887-47a2-8ac5-f4d617e911b7.png)
 
 
 After running the command 
 $docker images
 $doker ps
 $docker ps -a
 $docker container list
 
 ![image](https://user-images.githubusercontent.com/55473846/170988304-c9af96bf-5423-43c4-9444-b6f9c3d3e2b9.png)
 
 
 And finally after pulling the images a conatiner image was formed and on the browswer when we  call the command
 curl localhost:8080
 or on the broswer
 localhost:8080
 the below was shown
 
 
![image](https://user-images.githubusercontent.com/55473846/170988460-bde88007-c42d-4398-a8f0-0a6cfa3022c2.png)
 
 
 
