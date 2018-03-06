# Docker mariadb for ESCO use

Container docker MariaDB + phpMyAdmin

It provides an easy to use of the mariadb database with a configuration close to production. (in strict mode only expect if an evolution come)
But don't use it in production, the mariadb root user doesn't has restriction access (permission are setted on 'root'@'%') !


## Requirements

[Docker](https://www.docker.com/) and [docker-compose](https://docs.docker.com/compose/) are used to setup the technical environment containing all requirements.

For linux install : see documentation [Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-using-the-convenience-script) and [Docker-compose](https://docs.docker.com/compose/install/#prerequisites)


## Setting up the environment

* Clone the github repository


```bash
git clone git@github.com:GIP-RECIA/docker-mariadb.git
```

* Download required docker images

```bash
docker-compose pull
```

* Build custom docker images

```bash
docker-compose build
```

* Start containers

```bash
docker-compose up -d
```

* Shutdown the environment

```bash
docker-compose down
```

or

```bash
docker-compose down -v  # All data will be lost !
```

also is working

```bash
docker-compose stop
```

## Services

- MariaDB should be accessible with mysql command :

	```bash
	mysql -h 127.0.0.1 -u root -proot
	```

	or by docker native network :

	```bash
	mysql -h 127.17.0.1 -u root -proot
	```

- PhpMyAdmin should be accessible from browser url : [http://127.0.0.1:8181/](http://127.0.0.1:8181/) or by docker native ip : [http://127.17.0.1:8181/](http://127.17.0.1:8181/)

## Check to make

After running first time ```docker-compose up -d``` you should check :

- if all services are accessible
- on mysql you should have all databases intiated (3 native mariadb database) and with the ```test``` database initialized from the default script provided in ```.docker/mariadb-strict/dump/```