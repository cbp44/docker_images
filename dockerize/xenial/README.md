# cbp44/dockerize:xenial

## Command line usage

```sh
# Displays dockerize help
docker run --rm cbp44/dockerize:xenial --help
```

## Dockerfile usage

```dockerfile
FROM cbp44/dockerize:xenial as dockerize

# Waits until google.com is reachable inside of the container and runs echo command if it eventually is reachable. If it isn't reachable in 10 seconds, the container exits with failed exit status.
CMD dockerize -wait http://google.com && echo "Hello World"
```