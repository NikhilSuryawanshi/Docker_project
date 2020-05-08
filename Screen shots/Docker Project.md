#                 DOCKER PROJECT

In this project i have integrated a java web based application to Docker container

This docker project is a web based dynamic java application which is running on the Apache tomcat server and for Database mysql server is used .

 For this project basic requirement which we needed is a docker for fastest working environment . To install this we have to configure yum to install the docker . For this go to the Terminal or Rhel8 and type following command :

![ss 0]("0.png")

           $  gedit /etc/yum.repos.d/docker.repo 


here docker.repo is the name i have given to the repo but you can also give your desired name .

now you have to write this url in the created file

[docker]
baseurl=https://download.docker.com/linux/centos/7/x86_64/stable/
gpgcheck=0

after this save and exit the file.

    For installing the Docker you have to type the following command in terminal:

    $ yum install docker


or

    $  yum install docker-ce --nobest


![ss 1]("1.png") 

    Start the docker services by typing the following command ;

      $   systemctl start docker 


    Check docker is running by command :

       $  systemctl status docker 


![ss 2]("2.png")


    Now download the required pre-set Operating System environment image by the docker pull command :

![ss 3](3.png")


first i have pulled wordpress image , you can also pull your desired image by just putting the name at the end of the command $ docker pull <image-name>

here i have the following images:
![ss 4]("4.png")


    Now start the mysql server container by the following command :

![ss 5]("5.png")


here I have my project files developed in java are placed in the folder ~/Downloads/sss/ & /user/local/tomcat/webapps/ is the folder inside the container where i have link my sss folder inside webapps -p means port forwarding tomcat server runs on 8080 port it forwarded to port 1235 on host OS of container i.e Rhel8 IP .

After running the above commands server starts and show this type of Output
![ss 7]("7.png")


now check the container is properly running by command :


docker ps


![ss 8]("8.png")

here you can see ports ports of the tomcat is forwarded from 8080 to port 1235 and i have one more wordpress server which is running on port 80 and forwarded to port 1234.

    Now go to browser and see the web pages by typing the host OS ip:port i.e. in my case my host OS of container IP is 192.168.43.32 and port is 1235 , so go to this url http://192.168.43.32:1235 on your browser. The web page comes up.

![ss 9]("9.png")


here sssm is a folder which is our project name in this folder webcontent is also a folder created by eclipse ide for storing the web pages.

You can also create the wordpress site by some easy configurations for that you have to install the docker-compose type following command in terminal

curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

after this you have to change permission by this

sudo chmod +x /usr/local/bin/docker-compose

now after doing this you have to create a file name docker-compose.yml

and write this configuration in that file
![ss10]("10.png")


for launching the container you have to enter the following command in the same folder where the docker-compose.yml file is created :

docker-compose up -d

![ss11]("11.png")


then you will see the container started sucessfully now go to browser and type ip of host os and port , in my case my IP is 192.168.43.32 and port is 1234
![ss12]("12.png")

