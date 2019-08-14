# Dockerize

Dockerize is a utility to simplify running applications in Docker containers. Check out the `dockerize` [documentation](https://github.com/jwilder/dockerize#usage) for nice examples of how to use the `dockerize` program in your Docker images.

Here, I created Docker images using `ubuntu` as base with the [dockerize](https://github.com/jwilder/dockerize) program pre-installed at `/usr/local/bin/dockerize`.

#### Why make these images?
The images pushed by the creator of `dockerize` use `alpine` as the base image, and just copying `/usr/local/bin/dockerize` from `jwilder/dockerize` into an `ubuntu` image fails due to dependency issues. In a lot of my projects I use `ubuntu` base images.

## Using the Images
- **cbp44/dockerize:bionic** documentation is [here](bionic/README.md)
- **cbp44/dockerize:xenial** documentation is [here](xenial/README.md)

## Building them yourself
1. Clone the repository to your machine
2. Navigate to `./docker_images/dockerize`
3. Build the image you want
    ```sh
    # Build the bionic image
    make bionic
    # Build the xenial image
    make xenial
    # Build them both
    make all
    ```
