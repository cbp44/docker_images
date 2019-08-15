# dockerize ![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/cbp44/dockerize)

[Dockerize](https://github.com/jwilder/dockerize) is a very useful utility written by [Jason Wilder](http://jasonwilder.com/blog/2014/10/13/a-simple-way-to-dockerize-applications/) to simplify running applications in Docker containers.

> It allows you to:
>
> - Generate application configuration files at container startup time from templates and container environment variables
> - Tail multiple log files to stdout and/or stderr
> - Wait for other services to be available using TCP, HTTP(S), unix before starting the main process.

## Supported tags and respective `Dockerfile` links

- [`cbp44/dockerize:bionic`, `cbp44/dockerize:latest`](https://github.com/cbp44/docker_images/blob/master/dockerize/bionic/Dockerfile)
- [`cbp44/dockerize:xenial`](https://github.com/cbp44/docker_images/blob/master/dockerize/xenial/Dockerfile)

## Why create these images?
The [`jwilder/dockerize`](https://hub.docker.com/r/jwilder/dockerize) images are [`alpine`](https://hub.docker.com/_/alpine) based and just copying `/usr/local/bin/dockerize` from one of his images into an [`ubuntu`](https://hub.docker.com/_/ubuntu) image fails with dependency issues when you try running `dockerize`.

## Usage

#### Command line usage

```sh
# Displays dockerize help
docker run --rm cbp44/dockerize:latest --help
```

#### Dockerfile usage

```dockerfile
FROM cbp44/dockerize:latest as dockerize

# Waits until google.com is reachable inside of the container and runs echo command if it eventually is reachable. If it isn't reachable in 10 seconds, the container exits with failed exit status.
CMD dockerize -wait http://google.com && echo "Hello World"
```

See more usage examples [here](https://github.com/jwilder/dockerize#usage).
