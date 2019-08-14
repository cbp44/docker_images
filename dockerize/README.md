# Ubuntu images for dockerize

Dockerize is a utility to simplify running applications in Docker containers. Read about [dockerize](https://github.com/jwilder/dockerize).

This directory contains the code to create various Ubuntu-based Docker images with `dockerize` pre-installed. I created them because the images pushed by the creator of `dockerize` use `alpine` as the base image, and just copying `/usr/local/bin/dockerize` from `jwilder/dockerize` into an `ubuntu` image failed with dependency issues and in a lot of my containers I use `ubuntu` as the base image.

## Developing

These commands are mostly just for my reference in the future for how to build and publish the images to Docker Hub.

## Building

1. Clone the repository to your machine
2. Navigate to `./docker_images/dockerize`
3. Build the image you want
    ```sh
    # Example usage for building and running bionic version
    export UBUNTU_CODENAME=bionic
    # Build the dockerize:base image first
    docker build --build-arg BUILD_DATE=`date -u +"%Y-%m-%dT%H:%M:%SZ"` -t dockerize:base ./base
    # Build the Ubuntu dockerize image which uses the dockerize base image
    docker build --build-arg BUILD_DATE=`date -u +"%Y-%m-%dT%H:%M:%SZ"` -t dockerize:$UBUNTU_CODENAME ./$UBUNTU_CODENAME
    # Run the default command which is 'dockerize --help'
    docker run --rm dockerize:$UBUNTU_CODENAME
    ```

## Publishing to Docker Hub

```sh
export UBUNTU_CODENAME=bionic
export DOCKER_HUB_USERNAME=cbp44
docker login
# Tag and push the already built base image
docker tag dockerize:base $DOCKER_HUB_USERNAME/dockerize:base
docker push $DOCKER_HUB_USERNAME/dockerize:base
# Tag and push the already built Ubuntu image
docker tag dockerize:$UBUNTU_CODENAME $DOCKER_HUB_USERNAME/dockerize:$UBUNTU_CODENAME
docker push $DOCKER_HUB_USERNAME/dockerize:$UBUNTU_CODENAME
```
