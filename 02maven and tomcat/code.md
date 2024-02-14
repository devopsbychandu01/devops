# download the file and install java
tar -xvf <jdk file>
mv jdk1.8.0_202 java8

vi /etc/profile.d/java.sh

export JAVA_HOME=/opt/java8/
export PATH=$JAVA_HOME/bin:$PATH

source /etc/profile.d/java.sh
java -version

download tar.gz file
tar -xvf <gz File>
cd bin
sh startup.sh
sh shutdown.sh

./startup.sh status

## change the port number ##
vi ./conf/server.xml
# under connector change the value from 8080 to another port
# after this restrat the tomcat

### 403 error  ###
# now click on manager app you will get this error
cd webapp/manager/META-INF/context.xml
# allow your ip addresses or add the context under allow section  ".*"


### 401 error ###
cd conf/tomcat-users.xml
# here add your username and password
# restart tomcat




test.txt


scp test.jar username@<ip>:/opt/test.jar