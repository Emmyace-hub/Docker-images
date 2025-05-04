# Docker-images
Docker images are the building blocks of containers. they are lightweight, portable and self-sufficient packages that contain everything needed to run a software application, including codes, runtime, libraries and system tool

## step 1: pulling images from Docker hub
* Docker hub is a cloud-based repository that hosts a vast collection of Docker images.


* "docker search" : to explore availabe images on Docker Hub
![1](./img/1b.png)
* "docker pull"
![1](./img/3d.png)
* "docker images"
![1](./img/1a.png)

## step 2:  Creating a docker file
* using "nano" command to create qa new file (dockerfile)
![2](./img/2.png)
input script into the file:

       # Use the official NGINX base image
       FROM nginx:latest

       # Set the working directory in the container
      WORKDIR  /usr/share/nginx/html/

       # Copy the local HTML file to the NGINX default public directory
       COPY index.html /usr/share/nginx/html/

       # Expose port 80 to allow external access
       EXPOSE 80

       # No need for CMD as NGINX image comes with a default CMD to start the server

![2](./img/2a.png)
* append instruction into the "index.html" file 

      echo "Welcome to Darey.io" >> index.html
![2](./img/2b.png)

* Build an image from the dockerfile we created

      docker build -t dockerfile .
![2](./img/2c.png)

* verfiy the image was successfully built
    
      docker images 
![2](./img/2d.png)

* Run a container based on the NGINX image we created with the dockerfile
  
      docker run -p 8080:80 dockerfile
![2](./img/2e.png)


## step 3: create an EC2 instance
* on aws console we create a new EC2 instance and edit the security group to allow all incoming traffic associated to the security group, the aimm is to allow incoming traffic on port 8080docker

* create an EC2 named "doc-ec"
![3](./img/3a.png)
![3](./img/3b.png)
![3](./img/3c.png)

* list available containers "ps-a"
![3](./img/4a.png)
the image above shows  my container "dockerfile" is up
* login to Docker hub and create a repository "firstdi"
![4](./img/4c.png)
![4](./img/4d.png)
* Tag docker image 
![4](./img/4e.png)
* login to docker hub on the CLI using command "docker login -u emmyace7"
![4](./img/4f.png)
* push the image to docker hub using cmd "docker push "
![4](./img/4g.png)
* verify the image was pushed successfully to the repository
![4](./img/4h.png)

In summary i was able to create a new docker container and also push a docker image into the docker hub.