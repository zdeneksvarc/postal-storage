## About

**❗ This repository runs with the Postal [version 2.1.2](https://github.com/postalserver/postal/releases). It should be fine for version 2.1.x maybe 2.x**

The basic installation of the Postal mail delivery platform [requires](https://docs.postalserver.io/install/prerequisites) that the database server MariaDB and the message broker RabbitMQ are up and ready. Deploying this repository via Docker Compose will bring these prerequisites.

## Pre-requisites

Docker and Docker Compose

## Installation procedure

1. Destination directory will be `/opt/postal-storage`. Move to the subdirectory `cd /opt` and fetch the install repository `sudo git clone https://github.com/zdeneksvarc/postal-storage.git`. Finaly move to the destination directory `cd /opt/postal-tls`
2. Set the `MYSQL_ROOT_PASSWORD` and `RABBITMQ_DEFAULT_PASS` in the file `.env` in working directory. To generate passwords, you can use for example [pwgen](https://linux.die.net/man/1/pwgen), e.g. `pwgen 30 2 -y`
3. Start the postal-storage Docker Compose project via `docker compose up -d` and you're done 🎉

You can now proceed by [installing Postal](https://docs.postalserver.io/install/installation).

## A few notes

- This repository is called postal-storage, although RabbitMQ is not a typical database. It is a message broker. Still, the name postal-storage is good enough simple and appropriate.
- The default docker-compose.yml on which the basic Postal version 2.1.1 installation runs does not have a restart policy. Therefore, Postal services will not start after the host server is rebooted. You can set up the same restart policy as this postal-storage project has `restart: always`
- It's okay to be cautious about the trustworthiness of public docker images. If you consider it better, you can build the image of each of the three services used yourself.
