# cicd-pipeline

### 1. Install Docker on Ubuntu

Add Docker's official GPG key:
```
sudo apt-get update
```
```
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

Add the repository to Apt sources:
```
echo \
"deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
"$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
sudo apt-get update
```

To install the latest version, run:
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
```
sudo service docker status
```

### 2. Configure Docker Host with Remote API
```
sudo vi /lib/systemd/system/docker.service
```

Put string to `docker.service`: `ExecStart=/usr/bin/dockerd -H tcp://0.0.0.0:4243 -H unix:///var/run/docker.sock`

Restart Docker service:
```
sudo systemctl daemon-reload
sudo service docker restart
```

Validate API by executing below curl command:
```
curl http://localhost:4243/version
```

### 3. Configure Jenkins Server with Docker plug-in
`docker-agent`
`tcp://docker_host_dns:4243` -> `tcp://ec2-13-51-193-237.eu-north-1.compute.amazonaws.com:4243`

tcp://16.16.215.210:4243
curl http://16.16.215.210:4243/version

```
http://ec2-51-20-181-70.eu-north-1.compute.amazonaws.com:8080
http://51.20.181.70:8080
```

docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11
docker run --name jenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11

https://www.coachdevops.com/2022/08/jenkins-build-agent-setup-using-docker.html

AWS: EC2
Security Groups:
rule 1
ssh: TCP: 22
Anywhere:

rule 2
Custom TCP: TCP: 4243
Custom: 0.0.0.0/0:

rule 2
Custom TCP: TCP: 8080
Custom: 0.0.0.0/0:

rule 3
Custom TCP: TCP: 32768-60999
Custom: 0.0.0.0/0:


https://github.com/jaiswaladi246/docker-spring-boot-java-web-service-example
https://www.youtube.com/watch?v=BePJ1bBWk3E

https://www.youtube.com/watch?v=yb6DodK6mbg
https://www.youtube.com/watch?v=y-QqlBpLQ7k
https://www.youtube.com/watch?v=lOdrdV0eDrs&t=0s

sudo usermod -a -G docker ubuntu
sudo usermod -a -G docker jenkins
sudo service jenkins restart


Installing Jenkins:
sudo apt-get update
sudo apt-get install openjdk-11-jdk
wget https://updates.jenkins-ci.org/latest/jenkins.war
java -jar jenkins.war --httpPort=8080

Starting Jenkins:
sudo systemctl start jenkins.service
sudo systemctl status jenkins

sudo systemctl start jenkins.service
sudo systemctl restart jenkins

http://your_server_ip_or_domain:8080
Get password:
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

EcrRegistryFullAcceesEC2