# server
Instructions for server setup

# Setup steps
```bash
# update and upgrade remote
sudo apt-get update && apt-get upgrade

# install miniconda on remote: https://docs.conda.io/en/latest/miniconda.html
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh

# install and enable openssh-server on boot on remote 
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh

# transfer pub key from local to remote
scp key.pub user@ip:~/

# register key on remote
mkdir ~/.ssh && cat ~/key.pub >> ~/.ssh/authorized_keys

# disable password login --- set PasswordAuthentication to no
sudo apt-get install vim
sudo vim /etc/ssh/sshd_config

# restart ssh server
sudo systemctl restart ssh

# set up telegram bot to send ip on boot
```