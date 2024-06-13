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
ssh-keygen -t rsa

after this you will get public and private key.
cat public key.

# 2nd server
copy past the public keys into /root/.ssh/authorized_keys path
past the puclikey to the autherized keys.


# 2nd server
ssh-keygen -t rsa
get the public key 

# 1st server
copy past the public keys into /root/.ssh/authorized_keys path
past the puclikey to the autherized keys.

#### Note: make sure autherized keys are 600 permissions.



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



### ansible windows

# host machine
apt install python3-pip -y
pip3 install pywinrm

# windows server

# run the script "https://raw.githubusercontent.com/jborean93/ansible-windows/master/scripts/Upgrade-PowerShell.ps1"

[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$url = "https://raw.githubusercontent.com/jborean93/ansible-windows/master/scripts/Upgrade-PowerShell.ps1"
$file = "$env:temp\Upgrade-PowerShell.ps1"
$username = "devops"
$password = "India@123456"

(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force

&$file -Version 5.1 -Username $username -Password $password -Verbose

## next commands ##
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Force

$reg_winlogon_path = "HKLM:\Software\Microsoft\Windows NT\CurrentVersion\Winlogon"
Set-ItemProperty -Path $reg_winlogon_path -Name AutoAdminLogon -Value 0
Remove-ItemProperty -Path $reg_winlogon_path -Name DefaultUserName -ErrorAction SilentlyContinue
Remove-ItemProperty -Path $reg_winlogon_path -Name DefaultPassword -ErrorAction SilentlyContinue


## fix the hotfix
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$url = "https://raw.githubusercontent.com/jborean93/ansible-windows/master/scripts/Install-WMF3Hotfix.ps1"
$file = "$env:temp\Install-WMF3Hotfix.ps1"

(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)
powershell.exe -ExecutionPolicy ByPass -File $file -Verbose


## run following script
# https://raw.githubusercontent.com/ansible/ansible-documentation/ae8772176a5c645655c91328e93196bcf741732d/examples/scripts/ConfigureRemotingForAnsible.ps1


## 
winrm enumerate winrm/config/Listener


$thumbprint = "E6CDAA82EEAF2ECE8546E05DB7F3E01AA47D76CE"
Get-ChildItem -Path cert:\LocalMachine\My -Recurse | Where-Object { $_.Thumbprint -eq $thumbprint } | Select-Object *


$selector_set = @{
    Address = "*"
    Transport = "HTTPS"
}
$value_set = @{
    CertificateThumbprint = "E6CDAA82EEAF2ECE8546E05DB7F3E01AA47D76CE"
}

New-WSManInstance -ResourceURI "winrm/config/Listener" -SelectorSet $selector_set -ValueSet $value_set











[windows]
172.171.206.104
[windows:vars]
ansible_user=devops
ansible_password=India@123456
ansible_connection=winrm
ansible_winrm_server_cert_validation=ignore
