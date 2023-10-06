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

lscpu

top

df -h

ls
mkdir src

vi hellow.py
python3 hellow.py

5. Stop instance






