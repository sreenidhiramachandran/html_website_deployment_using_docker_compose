# html_website_using_docker_compose


Docker compose is a tool for defining and running multi-container Docker applications. With Compose, we use a yaml file to configure the application’s services. 


Features


Step 1:
Install docker

sudo yum install docker -y
sudo systemctl restart docker.service
sudo systemctl enable docker.service
sudo usermod -a -G docker ec2-user




Step 2:

Install Compose


Download the necessary files from github and provide execute privileges
sudo curl -SL https://github.com/docker/compose/releases/download/v2.6.0/docker-compose-linux-x86_64 -o /usr/bin/docker-compose
sudo chmod +x /usr/bin/docker-compose

We can then use the following command to see the compose version.
docker-compose version

![image](https://user-images.githubusercontent.com/120683482/216138213-d1475f8a-928a-4209-bdea-a2358e437df9.png)


Create a project directory, create a docker-compose.yml file and download a sample HTML website

mkdir compose-project; cd compose-project; 
git clone https://github.com/sreenidhiramachandran/html_website_using_docker_compose.git

wget https://www.tooplate.com/zip-templates/2121_wave_cafe.zip; unzip 2121_wave_cafe.zip; mv 2121_wave_cafe website; rm 2121_wave_cafe.zip;

[ec2-user@ip-172-31-45-117 compose-project]$ docker-compose up -d
![image](https://user-images.githubusercontent.com/120683482/216138958-740a3f0b-624c-4635-9a9e-b423143936f0.png)


$ docker-compose ps

![image](https://user-images.githubusercontent.com/120683482/216139675-cc8ccc22-ea1f-406f-b702-32c7113d3147.png)

$ docker container ls -a

![image](https://user-images.githubusercontent.com/120683482/216139835-1e406934-99ec-4587-ba91-8adec279c41b.png)






![image](https://user-images.githubusercontent.com/120683482/216137757-4361fa72-dfce-4e11-862a-9abbfcb760ca.png)
