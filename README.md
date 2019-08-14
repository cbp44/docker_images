# docker_images

This is a collection of useful Docker images I've created for use in various projects.

I have published all of the images to Docker Hub for easy usage as base images or as a way to copy executables / code from them into a multi-stage build `Dockerfile`.

These are under an MIT license so feel free to do whatever you want with them.

## The Images

### dockerize

Docker images using `ubuntu` as base with [dockerize](https://github.com/jwilder/dockerize) program pre-installed at `/usr/local/bin/dockerize`.

See [usage examples](dockerize/USAGE.md) for more help.
