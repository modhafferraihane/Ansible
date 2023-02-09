1) Méthode classique : install vscode, virtualbox, vagrant et pgadmin4 
2) Méthode innovante : install chocolatey 
Chocolatey for Business (C4B) est l'offre d'entreprise qui permet aux entreprises d'adopter une approche DevOps pour gérer leur environnement Windows, vous permettant de fournir des applications à vos utilisateurs de manière plus fiable et plus rapide.

 

First, ensure that you are using an administrative shell - you can also install as a non-admin, check out Non-Administrative Installation.
$ Run Get-ExecutionPolicy. If it returns Restricted, then run Set-ExecutionPolicy AllSigned or Set-ExecutionPolicy Bypass -Scope Process.
Now run the following command:
$ Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
$ choco install virtualbox
$ choco install vagrant
$ choco install pgadmin4
$ choco install vscode

3) Install VM with Vagrant 
Vagrant est un outil permettant de créer des environnements de développement complets. Avec un flux de travail facile à utiliser et une concentration sur l'automatisation, Vagrant réduit le temps de configuration de l'environnement de développement, augmente la parité développement/production et fait de l'excuse "ça marche sur ma machine" une relique du passé.
 



•	copier le fichier vagrantfile 
open cmd 
$ vagrant up
3) open new MV 
$ user : vagrant 
$ password : vagrant 
$ sudo -i 
•	Enable SSH on Ubuntu VM 
$  sudo nano /etc/ssh/sshd_config
In the file, find the PasswordAuthentication line and make sure it ends with yes.
Find the ChallengeResponseAuthentication option and disable it by adding no.
If lines are commented out, remove the hash sign # to uncomment them.
$ sudo systemctl restart sshd
•	Enable root login over SSH for vscode 
$  sudo nano /etc/ssh/sshd_config
In the file, find the PermitRootLogin yes line and make sure it ends with yes.
$ sudo systemctl restart sshd
•	connect to a virtual machine via SSH from Windows 10
open cmd 
$ ssh vagrant@10.1.12.x
$ password : vagrant
$ sudo -i 
•	Use SSH keys to communicate with GitLab
$ ssh-keygen 
$ yes yes .. .
$ cat /root/vagrant/.ssh/id_rsa.pub
copier le keyssh in gitlab
•	clone project from gitlab
$ git clone -b yourbranch url-ssh
$ cd /projet
$ docker-compose build 
$ docker -compose up 
$ docker exec -it app-django-container /bin/bash  
$# python manage.py migrate 
$# yarn 
$# yarn build
$# yarn watch

•	open pgadmin 4
La manière la plus pratique d’administrer des bases de données PostgreSQL est d’utiliser l’interface graphique pgAdmin4.
 
$ generale : name : app-db-container
$ connection : 
$ host name/database: postgres
$ port : 5432
$ username : postgres
$ : password : mypassword
$ save and connect


