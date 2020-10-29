# Jenk0nUbuPerfect
FIRST INSTALL JAVA
THEN SET JAVA_HOME PATH
sudo vi /etc/environment
add this line on newline
JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
source /etc/environment

Then intall jenins

sudo wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -

sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'

sudo apt-get update -y;

sudo apt-get install jenkins -y;sudo systemctl start jenkins;sudo systemctl enable jenkins;sudo systemctl status jenkins;

sudo su -  ## As a root set password for jenkins
passwd jenkins

EDITOR=vim visudo
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
jenkins ALL=(ALL) ALL

su - jenkins
to check sudo access
sudo ls -la /root

==========================================INSTALL-MAVEN-&-SET-MAVEN-HOME========================================    
cd /opt/
sudo wget https://mirrors.estointernet.in/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz

sudo tar -xvzf apache-maven-3.6.3-bin.tar.gz 

sudo mv apache-maven-3.6.3/ apache-maven/

ls

sudo rm -rf apache-maven-3.6.3-bin.tar.gz 

sudo update-alternatives --install /usr/bin/mvn maven /opt/apache-maven/bin/mvn 1001

cd /etc/profile.d/

sudo vim maven.sh

# Apache Maven Environment Variables
# MAVEN_HOME for Maven 1 - M2_HOME for Maven 2
export M2_HOME=/opt/apache-maven
export MAVEN_HOME=/opt/apache-maven
export PATH=${M2_HOME}/bin:${PATH}

sudo chmod +x maven.sh

source maven.sh


echo $M2_HOME

cd /opt/apache-maven

tHEN ON JENKINS DASHBOARD GOTO MANAGEJENKINS--CONFIGURE-GLOBAL-TOOLS- ADDJDK ITS HOME PATH
& ADD MAVEN AND ITS HOME PATH
THEN FOLLOW

newitem- maven project
GitHub project
https://github.com/adukdp/my-mvn-app/
Git
https://github.com/adukdp/my-mvn-app.git
GitHub hook trigger for GITScm polling
Delete workspace before build starts
Build-Step
Invoke top level maven 
select maven-3.6
Goal clean test
