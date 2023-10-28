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
`jenkins-agent`
`tcp://docker_host_dns:4243`


