# Set up cloud storage and FTP (vsFTP)
## Task 1 Install vsFTP command

``sudo apt update`` 

``sudo apt install vsftpd``

#### Verify vsFTP version 

``vsftpd -versions``

## Task 2 Allow FTP in the firewall

#### 2.1 Veify FW status

``sudo ufw status``

#### 2.2 Allow ports 20 and 21

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
![image](https://user-images.githubusercontent.com/121900164/214267691-1fdc09e4-430b-4e57-bdc6-f9509527c567.png)
