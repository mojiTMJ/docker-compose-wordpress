
# docker-Compose WordPress
###### You have to check each line
simple docker-compose to create fresh WordPress environment

[Inspired by -> Docker Compose and WordPress](https://docs.docker.com/compose/wordpress/)

### Easy Wordpress development with Docker and Docker Compose

## Starting a new project

Make sure you have the latest versions of **Docker** and **Docker Compose** installed on your machine.

Clone the repo or Copy the **docker-compose.yml** file from this repository into a blank folder.

In the file you may change the IP address (in case you run multiple containers) or the database.

Here we use MariaDB and WordPress docker official image

##### Create containers

Open a terminal and *cd* to the folder you have the docker-compose.yml and run:
```
sudo docker-compose up -d
```

This create 2 new folders beside your docker-compose.yml file.
* **db-data** - used to store and restore database dumps
* **site-app** - the location of your Wordpress files

The containers are now build and running. You should be able to access the Wordpress installation with the configured IP in the browser address. For convenience you may add a new entry into your hosts file.

##### Starting containers

You can start the containers with the up command in daemon mode (by adding **-d** as a param) or by using the start command:
```
sudo docker-compose start
```

##### Stopping containers
```
sudo docker-compose stop
```

##### Remove containers

To stop and remove all the containers use the **down** command
```
sudo docker-compose down --volumes
```
... or the **rm** command if the containers are stopped already.
```
sudo docker-compose rm
```

## Project from existing source

Copy the docker-compose.yml file into a new directory. In the directory you create two folders:
* **db-data** - here you add the database dump
* **site-app** - here you copy your existing wordpress code

You can now use the **up** command:
```
sudo docker-compose up
```

This will create the containers and populate the database with the given dump. You may set your host entry and change it in the database, or you simply overwrite it in the **wp-config.php** by adding
```
define('WP_HOME','http://wp-app.local');
define('WP_SITEURL','http://wp-app.local');
```

## Creating database dumps
```
sudo ./export.sh
```

## Developing a Theme

Configure the volume to load the theme in the container in the docker-compose.yml

```
volumes:
  - ./theme-name/trunk/:/var/www/html/wp-content/themes/theme-name
```

## Developing a Plugin

Configure the volume to load the plugin in the container in the docker-compose.yml

```
volumes:
  - ./plugin-name/trunk/:/var/www/html/wp-content/plugins/plugin-name
```

### That's it Have Fun and don't Forgot to **STAR** this repo ;)

# MojiTMJ
