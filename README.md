docker_images ![MIT License](https://img.shields.io/badge/license-MIT-success)
=============

<img src="https://www.docker.com/sites/default/files/d8/2019-07/horizontal-logo-monochromatic-white.png" height="55" align="right" />
A collection of useful Docker images I've created for use in various projects.

All of these images have been published to [Docker Hub](https://hub.docker.com/) for easy usage as base images or as a way to copy software from them in a multi-stage build `Dockerfile`.

dockerize ![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/cbp44/dockerize)
---------
[Dockerize](https://github.com/jwilder/dockerize) is a very useful utility written by [Jason Wilder](http://jasonwilder.com/blog/2014/10/13/a-simple-way-to-dockerize-applications/) to simplify running applications in Docker containers.

> It allows you to:
>
> - Generate application configuration files at container startup time from templates and container environment variables
> - Tail multiple log files to stdout and/or stderr
> - Wait for other services to be available using TCP, HTTP(S), unix before starting the main process.

See usage examples [here](https://github.com/jwilder/dockerize#usage).

**Why create this?** The [`jwilder/dockerize`](https://hub.docker.com/r/jwilder/dockerize) images are [`alpine`](https://hub.docker.com/_/alpine) based and just copying `/usr/local/bin/dockerize` from one of his images into an [`ubuntu`](https://hub.docker.com/_/ubuntu) image fails with dependency issues when you try running `dockerize`.

| Image | Description |
| --- | --- |
| [`cbp44/dockerize:bionic`<br />`cbp44/dockerize:latest`](https://github.com/cbp44/docker_images/blob/master/dockerize/bionic/Dockerfile) | Official `ubuntu:bionic` image as base with `dockerize` installed.  |
| [`cbp44/dockerize:xenial`](https://github.com/cbp44/docker_images/blob/master/dockerize/xenial/Dockerfile) | Official `ubuntu:xenial` image as base with `dockerize` installed. |

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
