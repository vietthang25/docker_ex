# PheNet_Study - Example Docker 
## Docker Installation
### Step 1: Cài đặt [Docker Engine](https//docs.docker.com/engine/install/ubuntu/)
```
sudo apt-get remove docker docker-engine docker.io containerd runc

sudo apt-get update

sudo apt-get install \
apt-transport-https \
ca-certificates \
curl \
gnupg \
lsb-release

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
apt-cache madison docker-ce
sudo apt-get install docker-ce=<VERSION_STRING chosen from above> docker-ce-cli=<VERSION_STRING chosen from above> containerd.io docker-compose-plugin

sudo service docker start
sudo docker run hello-world
```

### Step 2: Cài đặt [Nvidia-docker2](https//docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)
```
curl https//get.docker.com/ | sh \
    && sudo systemctl --now enable docker

distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
       && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - \
       && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list

sudo apt-get update
sudo apt-get install -y nvidia-docker2
sudo systemctl restart docker
```
### Step 3: Cài đặt nvidia-cuda
```
sudo apt install nvidia-cuda-toolkit
```

### Step 4: [Sau khi cài docker](https://docs.docker.com/engine/install/linux-postinstall/)
```
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker 
docker run hello-world
```

### Step 5: Cài đặt nvidia-driver
```
sudo apt update
sudo apt upgrade
sudo apt install nvidia-driver-470
```