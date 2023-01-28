# Lab 2. Set FTP (vsFTP) server
## Task 1 Install vsFTP command

``sudo apt update`` 

``sudo apt install vsftpd``

#### Verify vsFTP version 

``sudo vsftpd -versions``

## Task 2 Allow FTP in the firewall

#### 2.1 Veify FW status

``sudo ufw status``

#### 2.2 If command not found, set up ufw (Uncomplicated Firewall)

``sudo apt install ufw``

Change values to enable IPv4 and IPv6 ports

``sudo nano /etc/default/ufw``

``IPV6=yes``

``IPV4=yes``

After modifying, press ctrl + x then press Y and hit Enter to save

To change policies ``sudo ufw default [policy] [chain]`` search this topic yourself

Verify status again ``sudo ufw status``

If status "inactive", activate it ``sudo ufw enable``

Verify status again ``sudo ufw status``

#### 2.3 Allow ports 20 and 21

``sudo ufw allow 20/tcp``

``sudo ufw allow 21/tcp``

#### Verify status again

``sudo ufw status``

## Task 3 Configure FTP access

#### 3.1 Create copy of vsftpd.conf file

``sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.orig``

#### 3.2 Modify vsftpd.conf file

``sudo nano /etc/vsftpd.conf``

#### 3.3 Modify parameters/values as follows:

``listen=NO

listen_ipv6=YES

anonymous_enable=NO

local_enable=YES

write_enable=YES

dirmessage_enable=YES

use_localtime=YES

xferlog_enable=YES

connect_from_port_20=YES

chroot_local_user=YES

secure_chroot_dir=/var/run/vsftpd/empty

pam_service_name=vsftpd

rsa_cert_file=/etc/ssl/private/vsftpd.pem

rsa_private_key_file=/etc/ssl/private/vsftpd.pem

ssl_enable=YES

user_sub_token=$USER

local_root=/home/$USER/ftp

userlist_enable=YES

userlist_file=/etc/vsftpd.user_list

userlist_deny=NO``

#### Ctrl X + Y + Enter to save changes (It might be different)

## Task 4 Creat and Add FTP user

``sudo adduser tester``

``sudo passwd tester``

#### 4.1 Add the new user to the allowed FTP users list

``echo "tin" | sudo tee -a /etc/vsftpd.userlist``

#### 4.2 Restart VSFTPD service

``sudo systemctl restart vsftpd``

#### (Optional) To enable vsFTP at startup

``sudo systemctl enable vsftpd``

## Task 5 test this service; In this exercise, we'll use "Filezilla"

#### 5.1 Install Filezilla

``sudo apt install filezilla``

#### 5.2 launch FileZilla, either through the command line or GUI
``filezilla``

#### 5.3 Try connecting with the "tester" user you created

#### 5.4 Look up IP of your server 

``ip a``

#### 5.5 In the Filezilla window, type the IP address of the FTP server, username, and password in their respective fields

#### 5.6 Click Quick connect to connect to the vsftpd FTP server
