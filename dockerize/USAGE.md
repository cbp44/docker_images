# Usage of dockerize images

## Using it as a base image in your own Dockerfile

```dockerfile
FROM cbp44/dockerize:bionic as dockerize

# Example simple usage to wait for http://localhost:1234 service to be up and reachable inside of the container on start before executing a command
CMD -wait http://localhost:1234 && echo "Hello World"
```

## Building and running from source Dockerfile

1. Clone the repository to your machine
2. Navigate to `./dockerize`
3. Build the image you want
    ```sh
    # Example usage for building and running bionic version
    export UBUNTU_CODENAME=bionic
    docker build --build-arg BUILD_DATE=`date -u +"%Y-%m-%dT%H:%M:%SZ"` -t dockerize:$UBUNTU_CODENAME ./$UBUNTU_CODENAME
    docker run --rm dockerize:$UBUNTU_CODENAME
    ```

## Publishing to Docker Hub

These commands are mostly just for my reference in the future for how to publish the image to Docker Hub.

```sh
export UBUNTU_CODENAME=bionic
export DOCKER_HUB_USERNAME=cbp44
docker login
docker build --build-arg BUILD_DATE=`date -u +"%Y-%m-%dT%H:%M:%SZ"` -t dockerize:$UBUNTU_CODENAME ./$UBUNTU_CODENAME
docker tag dockerize:$UBUNTU_CODENAME $DOCKER_HUB_USERNAME/dockerize:$UBUNTU_CODENAME
docker push $DOCKER_HUB_USERNAME/dockerize:$UBUNTU_CODENAME
```
