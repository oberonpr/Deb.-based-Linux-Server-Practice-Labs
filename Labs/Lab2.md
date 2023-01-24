# Lab 2 Set FTP (vsFTP) server
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
