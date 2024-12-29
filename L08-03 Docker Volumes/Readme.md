# L08-03

## Open a terminal and create a volume

    docker volume create myvol

## List the volumes

    docker volume ls

## Run a Nginx container that will use the volume

    docker run -d --name voltest -v myvol:/app nginx:latest

## Connect to the instance

    docker exec -it voltest bash

    If Docker container you're trying to access doesn't have bash installed, its a common issue and can be resolved by using sh instead of bash. Here's how you can do it:
    docker exec -it <container_name> /bin/sh
    Replace <container_name> with the name of your container. This command uses sh, which is typically available in most containers

## Let’s create a file in the volume using Nano

    apt-get update # For Debian/Ubuntu-based containers
    apt-get install nano # For Debian/Ubuntu-based containers

    apk update # For Alpine-based containers
    apk add nano # For Alpine-based containers

## Create a file in the app folder

    cd app
    nano test.txt

Type something, save the file and exit Nano using:

    CTRL-O
    CTRL-X

Detach from the instance:

    exit

## Stop and remove the container

    docker stop voltest
    docker rm voltest

## Run it again and see if the file still exists

    docker run -d --name voltest -v myvol:/app nginx:latest
    docker exec -it voltest bash
    cd app
    cat test.txt

## Cleanup

    docker volume rm myvol
    docker stop voltest
    docker rm voltest
