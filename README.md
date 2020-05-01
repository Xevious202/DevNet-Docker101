# DevNet-Docker101
A guide for anyone to start their own Docker tutorial

Requirements:
Google Cloud [Account}
Personal/work computer

# THIS DOCUMENT IS CURRENTLY A WORK IN PROGRESS
### Warning: This document has high entropy, last valid test TBD

## Create your Google Cloud [Account]
1. Click on above link
  * Get through payment to free trial (if you haven't used google cloud)
  * Enable billing (you won't be charged if within your trial window)
2. Deploy the VM
  * Arrive at Google Cloud Console
  * In top search bar type `Ubuntu focal` and select the result
  * Click `Launch`
  * Change Firewall and Region options
    * Select a region close to you
    * Allow HTTP and HTTPS Traffic (if you choose to keep this environment change this to HTTPS only after this tutorial)
  * Click `Create` at the bottom of the page
    * You will land on the `VM Instances` page
  * Select `Connect -> Open in Browser Window` to open SSH session
3. Copy down the `External IP` field!
  
## Install [Docker] CE
1. Uninstall old versions
  * `$ sudo apt-get remove docker docker-engine docker.io containerd runc`
2. Update 'apt' package index
  * `$ sudo apt-get update`
3. Install packages to allow apt to use a repository over HTTPS
```sh
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```
4. Add Docker's Official GPG key
  * `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
5. Verify key fingerprint [9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88]
  * `$ sudo apt-key fingerprint 0EBFCD88`
6. Perform architecture specific install (arm64 below, others in source document, link in docker header)
  * **NOTE**: 'bionic' is a temporary fix until 20.04 is supported by Docker, check install link before running!
```sh
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   bionic \
   stable"
```
  * Use `uname -m` to determine your architecture
7. Install Docker CE
  * `$ sudo apt-get update`
  * `$ sudo apt-get install docker-ce docker-ce-cli containerd.io`
8. Enable docker on startup
  * `$ sudo systemctl enable docker`

## Deploy your first [container]!
1. From SSH Terminal
  * type and enter `$ sudo docker run -dp 80:80 dockersamples/101-tutorial`
2. Open your web browser and go to `http://<your external ip>`
  
## Follow the Guide

[Google}: <https://cloud.google.com/

[Docker]: <https://docs.docker.com/engine/install/ubuntu/>

[container]: <https://github.com/dockersamples/101-tutorial>
