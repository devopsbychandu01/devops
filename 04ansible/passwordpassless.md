1) create 2 servers
2) add users for both servers
3) vi /etc/ssh/sshd_config

permitRootLogin prohibited-password     --> has to be uncomment

systemctl restart sshd
systemctl restart ssh

#go to 
sudo visudo
test ALL=(ALL) NOPASSWD:ALL

## do the same process to the second server


# 1st server
su <created user>
sudo mkdir /home/test

ssh-keygen -t rsa

after this you will get public and private key.
cat public key.

# 2nd server
su <user>
sudo mkdir .ssh
sudo touch authorized_keys

past the puclikey to the autherized keys.


ssh-keyget -t rsa
get the public key 

#1st server copy the public key of the second server into authorized_keys
touch authorized_keys
edit authorized_keys and update second server public keys.


##Ansible install
apt-get update
apt-get install ansible -y
ansible --version
which ansible

vi /etc/ansible/hosts
[webserver]
<publickIP> ansible_ssh_user=root ansible_ssh_pass=<rootpassword>

## 20.119.249.62 ansible_ssh_user=root ansible_ssh_pass=India@123456 ##



# write the file
ansible-playbook <filename> --syntax-check

apt-get install sshpass

ansible-playbook <file>