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
***Stage-01 : Install Jenkins server and installed some plugin like docker pipeline, sonarqube scanner sonarqube  gerit , k8s continous deploy plugin 




***Stage-01 : Install Jenkins and start Jenkins***
Jenkins Installation Prequuisities https://www.jenkins.io/doc/book/installing/linux/

***Push all the web application page code file into github ***

![scprojectdevops1](https://user-images.githubusercontent.com/122585172/223335072-ce7e3e89-38c8-405f-a2f7-0d46cbf86ba4.png)


1:Installation guide is available here:- https://www.jenkins.io/doc/book/installing/linux/#debianubuntu
docker installation is here :- https://docs.docker.com/engine/install/ubuntu/ 

2: After installation, install suggested plugins

3: Open Jenkins Dashboard and install required plugins – SonarQube Scanner, sonar quality gate, dockerpipeline 

 4:-go to manage jenkins > manage pulgins > search for plugins > install without restart


![12 04 2023_17 13 09_REC](https://user-images.githubusercontent.com/122585172/231446875-4d984f89-f7ad-4673-812e-ef1c7da8987c.png)

***step 02:-SonarQube Server Installation***


Instead of whole step  follow installtion of sonarqube what you will do you will  do use sonarqube image in dockerhub registory.

  ***docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube*** 
  for sonarqube server you will long configration you much do  database and all in order install sonarqube so for the easy way what you will doing you will donig docker conatiner for the sonarqube access.
  
  
![12 04 2023_17 15 22_REC](https://user-images.githubusercontent.com/122585172/231447745-cbb5351f-4467-49be-8927-4ecf25a55df6.png)

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


![12 04 2023_17 20 40_REC](https://user-images.githubusercontent.com/122585172/231448731-7d0d105c-da12-4da7-a38d-a59deabbd9d3.png)


***step 04:- you must  do server setup master(k8s) and worknode(k8s) for kubernetes***
for this you can follow link:- https://www.youtube.com/watch?v=o6bxo0Oeg6o



![12 04 2023_17 26 35_REC](https://user-images.githubusercontent.com/122585172/231449983-8edf3176-1b32-4515-911b-2240d30a9a98.png)

***step 04: Make sure you must have dockerhub account for finding conatiner images .

![asd](https://user-images.githubusercontent.com/122585172/223350832-30e41a03-881c-4d7c-99a6-6a6a03e7cf17.png)


***step 05:- Docker installtion***

https://docs.docker.com/engine/install/ubuntu/


***step 06:- Helm charts installtion***

curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3

chmod 700 get_helm.sh

./get_helm.sh


![12 04 2023_17 32 58_REC](https://user-images.githubusercontent.com/122585172/231451506-8cacc7c4-b78f-483e-9a28-5c7cd8c03acd.png)


***step 07:- datree.io installtion***

curl https://get.datree.io | /bin/bash
datree version
datree test <your_kubernetes_manifest_YAML_NAME>



***datree.io dashbord***


![12 04 2023_17 37 02_REC](https://user-images.githubusercontent.com/122585172/231452898-889949db-3de8-4c37-b16d-95120dd10bea.png)

***Done with Installation , Now will we integrate all the tools with Jenkins***





 5:- After install plugin you have to go manage jenkins and then go configure system provide sonarqube url and some authentication token


![12 04 2023_17 45 02_REC](https://user-images.githubusercontent.com/122585172/231454156-84afe935-6768-4f62-8b47-ef5d9c1abd62.png)

6:- Here you have add the authentication token just click on that


![12 04 2023_17 48 06_REC](https://user-images.githubusercontent.com/122585172/231454838-57d65a2b-ce55-4c03-a9a4-e7d4f096e538.png)

7:- Here you have provide some secreat so how will we get that, Go to sonarqube go to administration and got to security option and then  genrate token 


![12 04 2023_17 50 48_REC](https://user-images.githubusercontent.com/122585172/231455488-65a08e69-cd4b-4ef4-90f4-3792544f03b6.png)

8:- Genrated sonarqube token make sure you put it jenkins secreat section and give meaningfull name 


![12 04 2023_17 57 15_REC](https://user-images.githubusercontent.com/122585172/231456834-5935d701-b867-4e42-b549-afa856d320e2.png)


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


![tryry](https://user-images.githubusercontent.com/122585172/231349469-38374a38-223a-4c29-a871-9f5b1f31d076.png)

 
 14:-once you will choose this then copy and paste it jenkinsfile where you have wrote 
 
 ![vf](https://user-images.githubusercontent.com/122585172/223038656-20c8b4b5-45e6-4ace-876b-df09826826c9.png) -->
 
15:-Configure nexus server in jenkins server


![RTERTE](https://user-images.githubusercontent.com/122585172/231445016-1c9df741-98c1-4b6c-9b87-46c31498b952.png)


16:- configration mail server in jenkins
first thing you have to do ,you have installed email extension and then configure your email extension

![tryry](https://user-images.githubusercontent.com/122585172/231349469-38374a38-223a-4c29-a871-9f5b1f31d076.png)


17:- also which ever the mail you use for authentication in that mail setting "Less secure apps access" should be enabled

![jhk](https://user-images.githubusercontent.com/122585172/223624942-7b19c722-f85f-423c-846b-f437d426a878.png)

18:- connect k8s with jenkins
![ythyt](https://user-images.githubusercontent.com/122585172/227117803-49e55efe-c77f-49eb-ad2b-f3ebbff7111c.png)

***We integrated all the tools with Jenkins, Now Create a declarative jenkins pipeline for each stage.***

General Jenkins declarative Pipeline Syntax

STAGE 2:- Define Stage as a Quality Gate stage
1:-I did not  do any kind of  maven installation are configration realted to maven why because let say example jenkins is used for multipal teams to deploy their application ,they want differnt differnt version of maven  so thats why i don't want to install it so whenever they wanted in the jenkins host  docker is inatlled , they can use docker as a agent anfd they can run their port

2:- genrated pipeline script for withsonarqualityenv
3:- once this is done what i  need to is i will gonna sh and i will give a permission sh 'chmod 777 maven' file agin what one more command i want to exute this which is sh './maven sonarqube' which help me pushing the code to sonarqube so their we will gonna check and  validate  aginest the sonarqube 

![gfhyj](https://user-images.githubusercontent.com/122585172/223633732-e864c480-5648-4fae-b233-f1d7c2e547d5.png)


***STAGE 2:- Docker Bulid & Docker Push to Nexus Repo*** 
***1:-What  is our next stage , our next stage is we will do docker build and push to which repo nexus repo right***
***2:- so I will not using any public repository here to store my docker images , so i will using my private hosted repository where i will creating  my repo and i will expose some ports so that all we will see here***
***3:- so now what are the setup you have to do in order to achive this thing so how will you do that ?***
***so for docker build you need what , you need a docker file so lets create a docker file so that we can compile our code***

***Docker file***
***it's docker file basically multistage docker file so in the first we will compile the code and get the artifact and in the next we will copying the artifact***

![qew](https://user-images.githubusercontent.com/122585172/224467183-e9e97080-7865-4c64-9691-a66acd616610.png)

4:- so lets add the command  so that it can compile or it can run the docker file and create image for us.
so i will use here multi line shell script


![ads](https://user-images.githubusercontent.com/122585172/224885767-d634d279-b28a-458a-b61b-62815cd888f5.png)

![ik](https://user-images.githubusercontent.com/122585172/224467565-d4016a14-a1fb-4766-a2cd-9155aaa4d9f2.png)

***once your email configration is done ,you will be adding post block here means either is falied or sucessed this blog should always run.***

***STAGE 3:- indentifying misconfigs using datree in helm charts ***
1:- I want to go inside the kubernetes directory and then i want to excute the command in that case i have one step template  which is like lets go to snippet genrator 

![gffg](https://user-images.githubusercontent.com/122585172/224882657-dc1ea7ce-3ff8-4cd4-bd1a-ebad4351b941.png)

2: and also verify to my helm charts aginest a datree rules so datree will hav e default rule so like a few enbaled and disbaled rules so first we will gonna excute the command and we will see what kinds of rules is enabled and in my helm charts which rules  are voileted. 
3:- we will going to add the command to my check helm charts whether all the rules in datree like verifyed or weither it will voileted
4: for that i will use datrre.io documnetaion and now take this command 
5: for check wether my helm charts work propely or not.


![ads](https://user-images.githubusercontent.com/122585172/224885793-6147181a-45f6-4bd8-96cd-610c3a28b6be.png)

![dfs](https://user-images.githubusercontent.com/122585172/224885819-f9ff28cd-5fb7-4251-a03c-55820b0d9f92.png)

***STAGE 4: pushing the helm charts to nexus***
1: i will gonna copy api so which push my helm charts on to the nexus.
     curl -u admin:$docker_password http://34.125.214.226:8081/repository/helm-hosted/ --upload-file myapp-${helmversion}.tgz -v
 2:- i will put docker pasword and nexus machine ip thats all
 3: once this is done the repository helm hosted make sure that whether your repository name itself or not
 4:- so now what we can do is we can version our file properly before pushing it so versioning what i  do is 
 
 ***STAGE 5: Deploying Application on  K8s cluster***
 ***Once push  is done we need to deploy helm charts into k8s cluster so thats means were deploying k8s manifest file on to the k8s cluster so for that what we need to do is we need to do few thing one as from the jenkins host i need to connect my k8s cluster other thing is in the k8s cluster I want to pull the images in my private repository so for we need to do few configration and also plugin also we need to install and also in the configration time you need to install kubectl in jenkins host
 and on  more thing in k8s cluster  for that what you need to do is go to k8s master and login in master and go to .kube folder of our users home directory and taken  cat config file this config file that we  required connect k8s cluster and after copy put in jenkins***

The next stage would be after the deployment I want to Verify whether my application is coming up or not those are the two stages I want to added in my pipeline .
Once approval is done then only it has  to be deployed.
Before deployment i want to add manual approval  part.

***STAGE 6: Manual Approval***
I want to give little  time kind of as soon as I send a request , They might be not approved , and also I don't want to wait for long time for example i want to give 10 minute of time limit were an like   with in that they want to approval for that i can do snippet genrator where search like timeout and take it , put it your code
10 minutes time for the approvers to approve this particular deployment if they don't approved it will be abort it.
and now next thing i want to send email which will have a build link also when they open that build link they should be able to approve the request.

***STAGE 7: Verifying App Deployment ***

I will create a another stage block which is verifying app deployment so see this is because once helm charts is done i want to verifying my application so that's why i am adding this so i added two stages on eis manual approval before the deployment and after the deployment I want  to verify my application is whether running or not ? so if exit when it executes if the exit status is 0 thats means it will gonna successfully rcome out of the stage and it will send success mail and if it's not working so the exit status will be non zero value it will gonna failed my pipleine so that is the logic here .

  ![DEPLOYK8S](https://user-images.githubusercontent.com/122585172/230598020-fc75b629-2319-49b6-8072-58541022846b.png)


Final outputs of this Project

Jenkins Output :

![devopsout](https://user-images.githubusercontent.com/122585172/230606025-983fd20c-cf74-43b0-8a62-2d3f21bff180.png)

Sonarqube Output:

![dsf](https://user-images.githubusercontent.com/122585172/230606378-5d5c5686-55c4-4a55-80c2-6de24c609f65.png)

Quality Gate Status in Jenkins:

![dsfgd](https://user-images.githubusercontent.com/122585172/230608358-88f5b67c-bf76-4fca-9c86-945f25efeba5.png)

Images in NexusRepository  pushed by jenkins:

![fgbhj](https://user-images.githubusercontent.com/122585172/230609469-103e7258-36ab-4dd6-b408-8c6f6f6000da.png)

pushing the helm charts to nexus outpt:

![reytreyrty](https://user-images.githubusercontent.com/122585172/230610608-e43d0d64-d644-471b-bd83-bc7d6c2b94bf.png)

Manual approval for Email output:

![gdhffhgf](https://user-images.githubusercontent.com/122585172/230610971-f6979542-15d3-4b27-80af-4d3b614ef53e.png)

Deploying application on k8s cluster output:V

![reytry](https://user-images.githubusercontent.com/122585172/230611450-e6a793d2-ab99-497c-87f6-668aabf38843.png)

Application output deployed in k8s:

![gfhgfghf](https://user-images.githubusercontent.com/122585172/230611635-e899681d-026e-44c0-ae48-0698fcb2f1d6.png)




  
  
  
  

 GFHGF
