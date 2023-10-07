1. Create account on https://www.oracle.com/ca-en/cloud/free/
1.1 Start for free
2. Create Compute instances Dashboard->Compute->instances
2.1. Download SSH key pair (private and public key) and to .ssh folder
2.1.1. Rename ssh key, adding instance name into ssh name.
2.2. Create
3. Instance dashboards Compute->Instances->Instance details->Work request
3.1. Start Instance
3.2. Copy Public IP address
4. Run ssh connection in PowerShell
ssh -i .\.ssh\ssh-key-instance-20231005-2117.key opc@192.18.148.37
5. Stop instance

6. Restart
6.1. Sing in to Oracle Cloud "illyakorotun" https://www.oracle.com/ca-en/cloud/sign-in.html
6.2. Open instance in Dashboard -> Compute-> Instances
6.3. Start
6.4. Run ssh connection in PowerShell
ssh -i .\.ssh\ssh-key-instance-20231005-2117.key opc@192.18.148.37
6.5. Stop instance

Linux command :
hostnamectl - Description of OS
lscpu - Display information about the CPU architecture
top - Show the Linux processes
df -h - Displays information about total space and available space on a file system.
ls - Lists all the files and directories under a specified directory 
lsblk - show hard disk size
free -th  - check RAM 

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

