***DevOps-Project***

In this project, I created an end-to-end CI/CD pipeline while keeping in mind Securities Best Practices, DevSecOps principles and used all these tools Git, GitHub , Jenkins,Maven, Junit, SonarQube, Docker, Trivy, AWS S3, Docker Hub, Kubernetes Nexus Repository, Helm charts, Datree.io  to achive the goal.

***Project Architecture***

<img width="16384" alt="SHRINIWAS DEVOPS  MEGA REAL TIME CICD PIPELINE PROJECT (2)" src="https://user-images.githubusercontent.com/122585172/223016565-173d4f9b-d822-42f6-a461-8bf993ee9a2c.png">


***CI/CD PIPELINE WORKFLOW***

<img width="8936" alt="hfg" src="https://user-images.githubusercontent.com/122585172/223016691-40826d3a-0884-4801-a75e-d00102664495.png">


***PreRequisites***
JDK
Git
Github
Jenkins
Sonarqube
Docker
Nexus Repository
Datree.io
Helm Charts
Maven
AWS account
Docker Hub account
Minikube & Kubectl
Kubernetes


***Want to create this Project by your own then Follow these project steps***

*** Installation Part***
***Stage-01 : Install Jenkins server and installed some plugin like docker pipeline, sonarqube scanner sonarqube  gerit




***Stage-01 : Install Jenkins and start Jenkins***
Jenkins Installation Prequuisities https://www.jenkins.io/doc/book/installing/linux/

***Push all the web application page code file into github ***

![scprojectdevops1](https://user-images.githubusercontent.com/122585172/223335072-ce7e3e89-38c8-405f-a2f7-0d46cbf86ba4.png)


1:Installation guide is available here:- https://www.jenkins.io/doc/book/installing/linux/#debianubuntu
docker installation is here :- https://docs.docker.com/engine/install/ubuntu/ 

2: After installation, install suggested plugins

3: Open Jenkins Dashboard and install required plugins – SonarQube Scanner, sonar quality gate, dockerpipeline 

 4:-go to manage jenkins > manage pulgins > search for plugins > install without restart

![cicdproject2](https://user-images.githubusercontent.com/122585172/223018773-9e57409c-e0c8-48d1-b724-7a0e755cad37.png)

***step 02:-SonarQube Server Installation***

Instead of whole step  follow installtion of sonarqube what you will do you will  do use sonarqube image in dockerhub registory.

  ***docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube*** 
  for sonarqube server you will long configration you much do  database and all in order install sonarqube so for the easy way what you will doing you will donig docker conatiner for the sonarqube access.
  
  ![we](https://user-images.githubusercontent.com/122585172/223341913-b74124be-9075-4619-899a-2f01eb85c167.png)

***step 03:- Nexus Repository installtion
for nexus you can follow this:-

apt-get update -y

echo "Install Java"
apt-get install openjdk-8-jdk -y
java -version

echo "Install Nexus"
useradd -M -d /opt/nexus -s /bin/bash -r nexus
echo "nexus ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/nexus
mkdir /opt/nexus
wget https://sonatype-download.global.ssl.fastly.net/repository/downloads-prod-group/3/nexus-3.29.2-02-unix.tar.gz
tar xzf nexus-3.29.2-02-unix.tar.gz -C /opt/nexus --strip-components=1
chown -R nexus:nexus /opt/nexus

nano /opt/nexus/bin/nexus.vmoptions
vi /opt/nexus/bin/nexus.rc
you can put nexus as a user

for start nexus you will do
sudo -u nexus /opt/nexus/bin/nexus start

![tytr](https://user-images.githubusercontent.com/122585172/223345481-e18df0ad-4649-4128-b744-53ecf16dbae6.png)

***step 04:- you must  do server setup master(k8s) and worknode(k8s) for kubernetes***
for this you can follow link:- https://www.youtube.com/watch?v=o6bxo0Oeg6o

![vbvcn](https://user-images.githubusercontent.com/122585172/223349891-f3709a38-0c65-4b4c-9d14-436253d35306.png)


***step 04: Make sure you must have dockerhub account for finding conatiner images .

![asd](https://user-images.githubusercontent.com/122585172/223350832-30e41a03-881c-4d7c-99a6-6a6a03e7cf17.png)


***step 05:- Docker installtion***

https://docs.docker.com/engine/install/ubuntu/


***step 06:- Helm charts installtion***

curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3

chmod 700 get_helm.sh

./get_helm.sh

![qwe](https://user-images.githubusercontent.com/122585172/223353379-cdf3268a-192d-41da-8cc5-1226bc5b2cca.png)


***step 07:- datree.io installtion***

curl https://get.datree.io | /bin/bash
datree version
datree test <your_kubernetes_manifest_YAML_NAME>

![olp](https://user-images.githubusercontent.com/122585172/223354911-e2387456-11a3-44e3-8ca4-845192ccd077.png)

***datree.io dashbord***
![werwt](https://user-images.githubusercontent.com/122585172/223356857-a3d77970-3b1d-459f-9e8b-f45fca3b6185.png)


***Done with Installation , Now will we integrate all the tools with Jenkins***





 5:- After install plugin you have to go manage jenkins and then go configure system provide sonarqube url and some authentication token

![CICDPROJECT3](https://user-images.githubusercontent.com/122585172/223026245-6262786b-4720-453d-817b-47379367ec42.png)

6:- Here you have add the authentication token just click on that

![PROJECT3CICD](https://user-images.githubusercontent.com/122585172/223027572-9ba09b85-5dd9-451e-b226-2890f0ff6b57.png)

7:- Here you have provide some secreat so how will we get that, Go to sonarqube go to administration and got to security option and then  genrate token 

![fgdgfrgr](https://user-images.githubusercontent.com/122585172/223028525-bdb1162c-f63d-4a8a-9dbc-2a90b1629e60.png)

8:- Genrated sonarqube token make sure you put it jenkins secreat section and give meaningfull name 

![rf](https://user-images.githubusercontent.com/122585172/223028952-59cb89b4-4429-4152-8f4e-4c2cc5b45c08.png)

9:- add sonartoken once this is done then apply and save

![rf](https://user-images.githubusercontent.com/122585172/223029529-28712b5b-8771-428c-bb34-abf58a42af0f.png

10:- One more thing what you have to do just go sonarqube and second thing go to configration here we will do two way handcheck first one jenkins will authenticate sonarqube token and second is sonarqube send logs confermation to jenkins and then go to configration and select webhook and you just need add jenkins url make sure 

![as](https://user-images.githubusercontent.com/122585172/223030593-78415166-a58d-4918-a33b-7753465f2a2e.png)


so this is all about the configrtaion between sonarqube and jenkins 


![rt](https://user-images.githubusercontent.com/122585172/223031332-3cb60957-2697-4954-aae8-7fbca0ae75b2.png)

11:- Now what you need jenkins should authenticate so create new job and give some meaningfull name and then select pipeline option after give job name



![yi](https://user-images.githubusercontent.com/122585172/223032038-139f97f1-3e98-4f5b-acfe-61d0167d7e92.png)

12:- once this is done you have just to go back and here instead of kepping of my pipeline script here what we will do I will take it from my github so select pipeline scm instead of scm i will choose git and then git you have to put github repo url

![io](https://user-images.githubusercontent.com/122585172/223033540-f46ba23d-4f06-46b1-9378-11c1ee05645e.png)

13:- you just have to genrate some pipeline script, you have just hit on sonarqubeEnv and then  you have to select  the authentication which you have configure write token  and genrate script
![gfj](https://user-images.githubusercontent.com/122585172/223623999-ebe1d372-a4f0-4b3f-b26c-5f978bf7d848.png)


 
 14:-once you will choose this then copy and paste it jenkinsfile where you have wrote 
 
 ![vf](https://user-images.githubusercontent.com/122585172/223038656-20c8b4b5-45e6-4ace-876b-df09826826c9.png) -->
 
15:-Configure nexus server in jenkins server

![TYR](https://user-images.githubusercontent.com/122585172/223622821-26be6a61-444f-4d29-b91c-e291a2e1fdea.png)

16:- configration mail server in jenkins
first thing you have to do ,you have installed email extension 


 
![gfj](https://user-images.githubusercontent.com/122585172/223624041-d6ec387b-51f0-4bd6-9516-572df5fd1b39.png)
