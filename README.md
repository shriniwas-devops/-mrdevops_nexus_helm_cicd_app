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

***Step: 1 Installation Part***
***Stage-01 : Install JDK and Create a Java Springboot application***
Push all the web application page code file into github

![scprojectdevops1](https://user-images.githubusercontent.com/122585172/223017209-69cfa96f-6d7b-4490-964b-45ebddd8aac2.png)

***Stage-02 : Install Jenkins and start Jenkins***
Jenkins Installation Prequuisities https://www.jenkins.io/doc/book/installing/linux/

1:Installation guide is available here:- https://www.jenkins.io/doc/book/installing/linux/#debianubuntu
docker installation is here :- https://docs.docker.com/engine/install/ubuntu/ 

2: After installation, install suggested plugins

3: Open Jenkins Dashboard and install required plugins – SonarQube Scanner, sonar quality gate, dockerpipeline 

4:-go to manage jenkins > manage pulgins > search for plugins > install without restart

![cicdproject2](https://user-images.githubusercontent.com/122585172/223018773-9e57409c-e0c8-48d1-b724-7a0e755cad37.png)

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

![ol](https://user-images.githubusercontent.com/122585172/223035743-25210541-37d7-4b0e-8186-8d1b2be10cbc.png)
 
 14:-once you will choose this then copy and paste it jenkinsfile where you have wrote 
 
 ![vf](https://user-images.githubusercontent.com/122585172/223038656-20c8b4b5-45e6-4ace-876b-df09826826c9.png)

