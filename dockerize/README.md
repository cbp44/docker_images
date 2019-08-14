## What is Dockerize?
Dockerize is a utility to simplify running applications in Docker containers. Check out the `dockerize` [documentation](https://github.com/jwilder/dockerize#usage) for nice examples of how to use the `dockerize` program in your Docker images.

Here, I created Docker images using `ubuntu` as base with the [dockerize](https://github.com/jwilder/dockerize) program pre-installed at `/usr/local/bin/dockerize`.

## Why make these images?
The images pushed by the creator of `dockerize` use `alpine` as the base image, and just copying `/usr/local/bin/dockerize` from `jwilder/dockerize` into an `ubuntu` image fails due to dependency issues. In a lot of my projects I use `ubuntu` base images.

## Usage

### Command line usage

```sh
# Displays dockerize help
docker run --rm cbp44/dockerize:latest --help
```

### Dockerfile usage

```dockerfile
FROM cbp44/dockerize:latest as dockerize

# Waits until google.com is reachable inside of the container and runs echo command if it eventually is reachable. If it isn't reachable in 10 seconds, the container exits with failed exit status.
CMD dockerize -wait http://google.com && echo "Hello World"
```
### Building them yourself
1. `git clone git@github.com:cbp44/docker_images.git`
2. `cd ./docker_images/dockerize`
3. Build the image you want
    ```sh
    # Build the bionic image
    make bionic
    # Build the xenial image
    make xenial
    # Build them both
    make all
    ```
