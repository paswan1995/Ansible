__Ansible Contd….__
* Lets try to install tomcat 10 on ubuntu 22.04 ReferHere: https://linuxize.com/post/how-to-install-tomcat-10-on-ubuntu-22-04/
* Ansible WOW (Ways of Working)
       * Ensure your manual steps are working
       * For each steps try to find a module which can help expressing desired state. 
* __Manual Steps__
 
```
sudo apt update
sudo apt-cache search openjdk
sudo apt install openjdk-11-jdk -y
java -version
* __Creating a System User__
sudo useradd -m -U -d /opt/tomcat -s /bin/false tomcat
VERSION=10.1.17
wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.17/bin/apache-tomcat-10.1.17.tar.gz -P /tmp
* Once the Tomcat tar file is downloaded, extract it to the /opt/tomcat directory:
sudo tar -xf /tmp/apache-tomcat-${VERSION}.tar.gz -C /opt/tomcat/
sudo ln -s /opt/tomcat/apache-tomcat-${VERSION} /opt/tomcat/latest
sudo chown -R tomcat: /opt/tomcat
* The shell scripts inside the Tomcat’s bin directory must be executable in order to run:
sudo sh -c 'chmod +x /opt/tomcat/latest/bin/*.sh'
* These scripts are used to start, stop and otherwise manage the Tomcat instance.
__Creating SystemD Unit File__
*Open your text editor and create a tomcat.service unit file in the /etc/systemd/system/ directory:
sudo nano /etc/systemd/system/tomcat.service
* Paste the following configuration:
```
[Unit]
Description=Tomcat 10 servlet container
After=network.target

[Service]
Type=forking

User=tomcat
Group=tomcat

Environment="JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64"
Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom -Djava.awt.headless=true"

Environment="CATALINA_BASE=/opt/tomcat/latest"
Environment="CATALINA_HOME=/opt/tomcat/latest"
Environment="CATALINA_PID=/opt/tomcat/latest/temp/tomcat.pid"
Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"

ExecStart=/opt/tomcat/latest/bin/startup.sh
ExecStop=/opt/tomcat/latest/bin/shutdown.sh

[Install]
WantedBy=multi-user.target
```
* Modify the JAVA_HOME variable if the path to your Java installation is different.
* Save and close the file and run the following command to notify systemd that we created a new unit file:

sudo systemctl daemon-reload
* Enable and start the Tomcat service:
sudo systemctl enable --now tomcat
* Check the service status:
sudo systemctl status tomcat
* The output should show that the Tomcat server is enabled and running:

```
● tomcat.service - Tomcat 10 servlet container
     Loaded: loaded (/etc/systemd/system/tomcat.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-12-24 18:53:37 UTC; 6s ago
    Process: 5124 ExecStart=/opt/tomcat/latest/bin/startup.sh (code=exited, status=0/SUCCESS)
   Main PID: 5131 (java)
...

* You can start, stop, and restart Tomcat the same as any other systemd service:
  
```
sudo systemctl restart tomcat
sudo systemctl stop tomcat
sudo systemctl restart tomcat

```
