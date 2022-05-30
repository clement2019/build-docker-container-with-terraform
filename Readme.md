## build-docker-container-with-terraform

# This project deals with the process of building an nginx docker conatiner image using terraform infrstructre as code tool
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

