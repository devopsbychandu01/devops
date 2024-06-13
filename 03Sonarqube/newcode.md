sysctl -w vm.max_map_count=524288

sysctl -w fs.file-max=131072

ulimit -n 131072

ulimit -u 8192

$ grep SECCOMP /boot/config-$(uname -r)

## update os
apt-get update

## install java 11
sudo apt-get install openjdk-17-jdk -y

java -version

sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" /etc/apt/sources.list.d/pgdg.list' Add the PostgreSQL signing key

sudo apt install postgresql postgresql-contrib -y

sudo systemctl enable postgresql
sudo systemctl start postgresql
sudo systemctl status postgresql

sudo passwd postgres
su - postgres
createuser sonar

psql
ALTER USER sonar WITH ENCRYPTED password 'India@123456';
CREATE DATABASE sonarqube OWNER sonar;
GRANT ALL PRIVILEGES ON DATABASE sonarqube to sonar;
\q
exit


sudo apt-get install zip -y


### download the sonarqube zip file of the community edition.

## https://www.sonarsource.com/products/sonarqube/downloads/?_gl=1*elynmg*_gcl_au*Mzk4NjQyMzI0LjE3MTY4MzAzNzc.*_ga*ODYzNzk2MzQ3LjE3MTY4MzAzNzc.*_ga_9JZ0GZ5TC6*MTcxNjkxMDUzMS4zLjEuMTcxNjkxMjY0OC41NC4wLjA.

## move the zip file to linux /tmp directory.

mv sonarqube-10.5.1.90531 (1).zip sonarqube-10.5.1.90531.zip
sudo unzip sonarqube-10.5.1.90531.zip
sudo mv sonarqube-10.5.1.90531 sonarqube
sudo mv sonarqube /opt/


sudo groupadd sonar
sudo useradd -d /opt/sonarqube -g sonar sonar
sudo chown sonar:sonar /opt/sonarqube -R







export SONAR_JAVA_PATH="/usr/lib/jvm/java-17-openjdk-amd64/bin/java"