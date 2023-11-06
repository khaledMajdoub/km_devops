# km_devops
#A Devops Projet by Khaled Majdoub that handles project testing ,deploying and monitoring using multiple CI/CD Tools 
5GAMIX-ESPRIT-2023


#first Steps 
open Powershell ( in administrator mode ) :
  go to the designated ubunto folder where the vagrant file exists:
  
```
vagrant reload
vagrant up
vagrant ssh
```
  in the Interactive mode inside of the ubuntu 22.04 Virtual machine :
  
  ```
sudo docker compose up -d
```
wait for all the services to be up ( it might take a while ) 

go 
  ```
http://localhost:8282/
```
    # RUN YOUR PIPELINE 
PS : port forwarding is enabled for each service to run on localhost with each designated one 
  consult the vagrantfile for more in the folder Devops/vagrantfile
