## install java 11
sudo apt-get install openjdk-11-jdk -y
java -version

#install maven
cd /opt wget https://dlcdn.apache.org/maven/maven-3/3.9.3/binaries/apache-maven-3.9.3-bin.tar.gz
tar -xvf <>
# update /etc/profile.d/maven.sh file with the following information
vi /etc/profile.d/maven.sh

export M3_HOME="/opt/apache-maven-3.9.3"
export PATH=$M3_HOME/bin:$PATH"

source /etc/profile.d/maven.sh
mvn --version

## Install and Configure PostgreSQL

sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main"   /etc/apt/sources.list.d/pgdg.list'
wget -q https://www.postgresql.org/media/keys/ACCC4CF8.asc -O - | sudo apt-key add -
apt install postgresql postgresql-contrib -y
systemctl enable postgresql
systemctl start postgresql
passwd postgres
su - postgres
createuser sonar

##Log in to PostgreSQL
psql
ALTER USER sonar WITH ENCRYPTED password 'India@123456';
CREATE DATABASE sonarqube OWNER sonar;
GRANT ALL PRIVILEGES ON DATABASE sonarqube to sonar;
\q

exit

## install zip
apt-get install zip -y

## Download the SonarQube distribution files.
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.6.1.59531.zip

##Unzip the downloaded file
unzip sonarqube-9.6.1.59531.zip

## move the file to /opt
sudo mv sonarqube-9.6.1.59531 sonarqube
sudo mv sonarqube /opt/

## create sonar user
adduser sonar

## permissions to that user
chown sonar:sonar /opt/sonarqube -R

## Configure SonarQube 
vi /opt/sonarqube/conf/sonar.properties 
# update the following

sonar.jdbc.username=sonar
sonar.jdbc.password=India@123456
Below those two lines, add the sonar.jdbc.url.

sonar.jdbc.url=jdbc:postgresql://localhost:5432/sonarqube

## Edit the sonar script file.
vi /opt/sonarqube/bin/linux-x86-64/sonar.sh
#update the following 
RUN_AS_USER=sonar

## Setup Systemd service

vi /etc/systemd/system/sonar.service


[Unit]
Description=SonarQube service
After=syslog.target network.target

[Service]
Type=forking

ExecStart=/opt/sonarqube/bin/linux-x86-64/sonar.sh start
ExecStop=/opt/sonarqube/bin/linux-x86-64/sonar.sh stop

User=sonar
Group=sonar
Restart=always

LimitNOFILE=65536
LimitNPROC=4096

[Install]
WantedBy=multi-user.target


systemctl enable sonar
systemctl start sonar
systemctl status sonar


## Modify Kernel System Limits

vi  /etc/sysctl.conf

#Add the following lines.
vm.max_map_count=262144
fs.file-max=65536
ulimit -n 65536
ulimit -u 4096


## Reboot the system to apply the changes.
reboot

## Access SonarQube Web Interface

http://<ip>:9000


# generate mvn project
mvn archetype:generate
mvn compile

## create sonar-project.properties file

# Required metadata
sonar.projectKey=java-sonar-runner-simple
sonar.projectName=Simple Java project analyzed with the SonarQube Runner
sonar.projectVersion=1.0

# Comma-separated paths to directories with sources (required)
sonar.sources=src

# Language
sonar.language=java

# Encoding of the source files
sonar.sourceEncoding=UTF-8


## create new project, generate token, choose the project language and copy the code


## finallyy run the sonarqube build command.

create quality profile and quality gate
