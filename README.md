# html_website_using_docker_compose


Docker compose is a tool for defining and running multi-container Docker applications. With Compose, we use a yaml file to configure the application’s services. 


## Features of Docker Compose
- Single host deployment - This means you can run everything on a single piece of hardware
- Quick and easy configuration - Due to YAML scripts
- High productivity - Docker Compose reduces the time it takes to perform tasks

## Step 1: Install docker

Install the package, start and enable the service. Also, I am adding 'ec2-user' to 'docker' group.
```sh
sudo yum install docker -y
sudo systemctl start docker.service
sudo systemctl enable docker.service
sudo usermod -a -G docker ec2-user
```


## Step 2: Install Compose


Download the necessary files from github and provide execute privileges
```sh
sudo curl -SL https://github.com/docker/compose/releases/download/v2.6.0/docker-compose-linux-x86_64 -o /usr/bin/docker-compose
sudo chmod +x /usr/bin/docker-compose
```

We can then use the following command to see the compose version.
```sh
docker-compose version
```
![image](https://user-images.githubusercontent.com/120683482/216138213-d1475f8a-928a-4209-bdea-a2358e437df9.png)

## Step 3:

Create a project directory, download the project files using git clone and move them to the project directory. 
```sh
mkdir compose-project; cd compose-project; 
git clone https://github.com/sreenidhiramachandran/html_website_using_docker_compose.git
mv html_website_using_docker_compose/* .
```
Download a sample HTML website and place them under a folder name 'website'
```sh
wget https://www.tooplate.com/zip-templates/2121_wave_cafe.zip; unzip 2121_wave_cafe.zip; mv 2121_wave_cafe website; rm 2121_wave_cafe.zip;
```

## Step 4: Create compose file

The Compose file is a YAML file defining version, services, networks, volumes, configs and secrets. 

Here, we are bind mounting the volume. 
```sh
vi docker-compose.yml
```
```sh
services:
  webserver:
   
    image: httpd:alpine
    container_name: sample_website
    restart: always
    networks:
      - mynetwork
    ports:
      - "8080:80"
    volumes:
      - "./website:/usr/local/apache2/htdocs/"

networks:
  mynetwork:
```
We can check the syntax using the below command.
```sh
docker-compose config
```

## Step 5: Start services

Using the below command, we start all the services defined in docker-compose.yml. In detached mode (-d), compose exits after starting the containers, but the containers continue to run in the background.

```sh
[ec2-user@ip-172-31-45-117 compose-project]$ docker-compose up -d
```
![image](https://user-images.githubusercontent.com/120683482/216138958-740a3f0b-624c-4635-9a9e-b423143936f0.png)


Using the below command, we can list the container created using docker-compose. 
>The contaioner created using docker-compose will be listed only if we run the ps command from the project directory.

```sh
$ docker-compose ps
```
![image](https://user-images.githubusercontent.com/120683482/216139675-cc8ccc22-ea1f-406f-b702-32c7113d3147.png)

Below command will list the container from any working directory. 

```sh
$ docker container ls -a
```

![image](https://user-images.githubusercontent.com/120683482/216139835-1e406934-99ec-4587-ba91-8adec279c41b.png)



>

> ## Screenshot of website create using docker-compose
>

![image](https://user-images.githubusercontent.com/120683482/216137757-4361fa72-dfce-4e11-862a-9abbfcb760ca.png)
