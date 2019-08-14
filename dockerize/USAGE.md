# Using the dockerize images

Check out the `dockerize` [documentation](https://github.com/jwilder/dockerize#usage) for nice examples of how to use the `dockerize` program in your Docker images.

## bionic

### From command line

```sh
# Displays dockerize help
docker run --rm cbp44/dockerize:bionic --help
```

### In a Dockerfile

```dockerfile
FROM cbp44/dockerize:bionic as dockerize

# Waits until google.com is reachable inside of the container and runs echo command if it eventually is reachable. If it isn't reachable in 10 seconds, the container exits with failed exit status.
CMD dockerize -wait http://google.com && echo "Hello World"
```

## xenial

### From command line

```sh
# Displays dockerize help
docker run --rm cbp44/dockerize:xenail --help
```

### In a Dockerfile

```dockerfile
FROM cbp44/dockerize:xenial as dockerize

# Waits until google.com is reachable inside of the container and runs echo command if it eventually is reachable. If it isn't reachable in 10 seconds, the container exits with failed exit status.
CMD dockerize -wait http://google.com && echo "Hello World"
```
