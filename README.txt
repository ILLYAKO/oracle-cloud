1. Create account on https://www.oracle.com/ca-en/cloud/free/
1.1 Start for free
2. Create Compute instances Dashboard->Compute->instances
2.1. Download SSH key pair (private and public key) and to .ssh folder and chenge owner to only one user in security file opption
2.1.1. Rename ssh key, adding instance name into ssh name.
2.2. Create
3. Instance dashboards Compute->Instances->Instance details->Work request
3.1. Start Instance
3.2. Copy Public IP address
4. Run ssh connection in PowerShell
ssh -i .\.ssh\ssh-instance-20231005-2117.key opc@192.18.148.37
5. Stop instance

6. Restart
6.1. Sing in to Oracle Cloud "illyakorotun" https://www.oracle.com/ca-en/cloud/sign-in.html
6.2. Open instance in Dashboard -> Compute-> Instances
6.3. Start
6.4. Run ssh connection in PowerShell
ssh -i .\.ssh\ssh-instance-20231005-2117.key opc@192.18.148.37
6.5. Stop instance

Linux command :
hostnamectl -- Description of OS
lscpu -- Display information about the CPU architecture
top -- Show the Linux processes
df -h -- Displays information about total space and available space on a file system.
ls -- Lists all the files and directories under a specified directory 
lsblk -- show hard disk size
free -th  -- check RAM 
dnf list installed  -- To list the installed packages on our system

mkdir src
vi hellow.py
python3 hellow.py

7. Docker 
(https://www.atlantic.net/dedicated-server-hosting/how-to-install-docker-and-docker-compose-on-oracle-linux-8/)
7.1. Update Oracle Linux Server
sudo dnf update -y
7.2. Install Docker CE
sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
sudo dnf install docker-ce -y
7.3. Post install (https://docs.docker.com/engine/install/linux-postinstall/)
7.3.1. Create the docker group
sudo groupadd docker
7.3.2. Add your user to the docker group
sudo usermod -aG docker $USER
7.3.3. Activate the changes to groups
newgrp docker
7.4 Start the Docker service
sudo systemctl start docker
7.5 Enable it to start at system reboot
sudo systemctl enable docker
7.6 Verivy the Docker running status
systemctl status docker
or
docker info
7.7 Verufy Docker installation
docker run hello-world
7.8. Check downloaded images
docker images
7.9 Check docker running containers
docker ps

8. Docker Compose
8.1. Install curl utility
sudo dnf install -y curl
8.2. Download latest Docker Composer version
sudo curl -L https://github.com/docker/compose/releases/download/v2.21.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
8.3. Set executable permission on the Docker Compose binary
sudo chmod +x /usr/local/bin/docker-compose
8.4. Verify Docker Composer version
docker-compose --version

9. If requered, Remove Docker and Docker Compose
systemctl stop docker
dnf remove docker-ce -y
rm -rf /usr/local/bin/docker-compose

10. Copy file 
10.1 Create directory /var/www
10.2 Change directory mode  to give read, write, and execute to everyone. 
chmod ugo+rwx foldername
10.3 Copy file index.html
 scp -i .\.ssh\ssh-instance-20231005-2117.key index.html opc@192.18.148.37:/var/www

11. Docker images hub
hub.docker.com
11.1 Found Apache http server httpd
11.2 Create Dockerfile in the project
vim Dockerfile
11.3 Add in Dockerfile
FROM httpd
COPY ./public-html/ /usr/local/apache2/htdocs/
11.4. Save and exit from editor
:wq!

12.1 Build Docker image
docker build -t website .
12.2 List of Docker images
docker images
12.3 Create running Docker container
docker run -itd -p 80:80 --name website website
12.4 Show running container list
docker ps
12.5  Add or Change Ingress Rulles in  Oracle Cloud->Dashboard->Networking->Virtual cloud networking->Security List Details->Ingress Rulles
Statelesss - unchecked
Source Type: CIDR
Source CIDR: 0.0.0.0/0
IP Protocol: TCP
Source Port Range: All
Destination Port Range: 80
Desctiption: Allow incoming requests from any IP addresses to port 80 - that will be mapped to the Docker Container.
12.6 access to container with public IP

????? https://medium.com/oracledevs/run-always-free-docker-container-on-oracle-cloud-infrastructure-c88e36b65610

------Kubernetes
1.0. Create new Instances "worker1"
1.1. Disable swap on instcances
sudo swapoff -a
1.2. Edit /etc/fstab and comment ## /swap
sudo vi /etc/fstab
??1.3 Install docker
??sudo apt install docker.io -y
 or 1.3. Install Docker CE
sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
sudo dnf install docker-ce -y
??? 1.4. Install curl
??sudo apt install apt-transport-https curl -y
?? sudo dnf install apt-transport-https curl -y
?? sudo dnf install curl -y - It was successfully updated
??sudo apt install curl -y
??1.5. Add repository key
??curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add
1.4. Install Kubernetes
sudo dnf config-manager --add-repo https://packages.kubernetes.io/yum/repos/kubernetes-el8-x86_64
sudo dnf install kubelet kubeadm kubectl



