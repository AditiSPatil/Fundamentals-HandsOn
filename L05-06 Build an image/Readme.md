# L05-06

We want to containerize a simple HTML page. To do that you’ll need to create a Dockerfile.

## Add a Dockerfile file

Add a new file and name it **Dockerfile** (without any file extension).

Copy and paste the following in the file and save it:

    FROM nginx:alpine
    COPY index.html /usr/share/nginx/html

## Build the image

    docker build -t your-image-name:tag-name -f /path/to/Dockerfile /path/to/build-context
    eg:1 docker build -t myapp-image -f C:\name\users\Documents\x1.dockerfile C:\name\users\Projects
    Note: tag-name is optional
    eg:2 docker build -t nginx-image:v1 -f "x1.dockerfile" .
    Note: In case of eg:-2, if build context and x1 file is in same folder from where you run docker build

### Multiple Build Contexts

    Docker also supports multiple build contexts, allowing you to use files from different directories. This can be done using the --build-context option with Docker BuildKit1.

    Example with Multiple Build Contexts
    docker build --build-context project1=C:\name\users\Projects1 --build-context project2=C:\name\users\Projects2 -t myapp-image .

    In this example, project1 and project2 are named build contexts that you can reference in your Dockerfile.

## list the images

    docker images

## Let's create an instance of the image

    docker run -d -p 8080:80 --name hello hello-world:v1

## List the containers running

    docker ps

## Display the page using curl

    curl localhost:8080

or use your browser. Navigate to https://localhost:8080

## Stop the container

Refresh the browser to confirm that it has stopped

    docker stop hello

## List the containers running

You should not see the hello-world:v1 instance anymore.

    docker ps

## Remove the instance from memory

    docker rm hello

## Confirm that the container is no longer running

    docker ps

## Is the image still present?

    docker images

## Delete the image

    docker rmi hello-world:v1
