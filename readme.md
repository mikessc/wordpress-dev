
# Wordpress Development Environment

The purpose of this repository is to provide a Wordpress Development Environment that can be used to create Wordpress themes and plugins.

##  Project folder
Create a new project folder with a name that is lowercase, no spaces, no dashes, no underscores.  Naming this folder correctly helps with the Docker setup.  

## Download the Files
To use this as a boilerplate for your project, download the files from the repository as a zip file and unpack them into your project folder. To contribute to this project, clone project, complete your work in a new branch and then submit your work as a Pull Request for peer review.

You should have this folder structure:
>project_name/docker-compose.yml
>project_name/readme.md
>project_name/uploads.ini
>project_name/wp-config.php


## Docker
Install [Docker](https://docs.docker.com/get-docker/) desktop. 

From your project folder, run the following command: 
>`docker-compose up -d`

Docker will read the instructions in ***docker-compose.yml***, and create three connected docker containers:
- Wordpress Web Server
- MySQL Database
- PhpMyAdmin 

The containers will be named based on your project folder's name, "project_name-wordpress-1", "project_name-db-1", "project_name-phpmyadmin-1". 

For bonus points, you could alternatively use this docker command to use a custom project name to instead of the folder name in the container names:
>`docker compose -p project_name up -d`

To stop running your project Docker containers, use the following command:
>`docker-compose stop`

Docker creates a ***wp-content*** folder inside your project directory. This is based on the Wordpress Docker Image.  The other Wordpress files are stored within the Docker Containers.

Docker also creates a ***mysql-data*** folder.  This contains the raw MySQL data files.  If you delete the containers from Docker, and create them again with that mysql-data folder in place, Docker will use that MySQL folder and your database will persist.

***uploads.ini*** allows you to override Apache php.ini settings, for example to allow larger file uploads. 

***wp-config.php*** is a copy of the default Wordpress Docker image Wordpress config file.  It has been altered to enable all debugging options, notably full React error messages in the console window.  

## Wordpress Frontend
If everything worked, you should see the Wordpress in a browser:
> http://localhost:8000/

Follow the instructions on that page to setup Wordpress and add an Admin user.

## Wordpress Admin
And you can access the Wordpress Admin pages here:
> http://localhost:8000/wp-admin/


## PhpMyAdmin
You can also access PhpMyAdmin to manage the database:
> http://localhost:8080/

The root password is defined in docker_compose.yml, so you should be able to login to PhpMyAdmin using:
> Login: root
> Password: somewordpress