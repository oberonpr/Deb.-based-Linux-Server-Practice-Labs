# Lab3 Set up SSH and RDP clients

## For this exercise, we'll use three clients; OpenSSH, FreeRDP, and Remmina

#### Task 1 Install FreeRDP

``sudo apt-get update``

``sudo apt-get install freerdp`` You can also specify which freeRDP version you want to download; ``sudo apt install freerdp2-x11``

#### Task 2 Install Remmina

``sudo apt update``

``sudo apt install remmina remmina-plugin-rdp remmina-plugin-secret remmina-plugin-spice``

#### Task 3 Install OpenSSH

``sudo apt-get update``

``sudo apt-get install openssh-server``

#### Task 3.1 Check your newly installed service

``sudo systemctl status sshd``

#### Task 3.2 Enabling SSH traffic on your firewall settings

``sudo ufw allow ssh``

#### Optional Task 3.3, Enable SSH server on system boot

``sudo systemctl enable ssh``

### Task 4 Try connecting to your "Secondary" VM through OpenSSH, Make sure your VM is up

#### Task 4.1 Search for this process at www.google.com or www.duckduckgo.com or any search engine

"How to connect through SSH Debian"
"How to connect through SSH Ubuntu"
