FROM cbp44/dockerize:base as dockerize

# Set the proper codename in the two FROM and ARG statements below
FROM ubuntu:xenial
ARG UBUNTU_CODENAME=xenial


LABEL maintainer="Chris Preusch"
# Info about this Dockerfile and the associated Docker image
LABEL org.label-schama.name="dockerize" \
      org.label-schama.version=$UBUNTU_CODENAME \
      org.label-schama.description="An ubuntu:${UBUNTU_CODENAME} image with dockerize pre-installed." \
      org.label-schama.license="MIT" \
      org.label-schama.docker.cmd="docker run --rm cbp44/dockerize:${UBUNTU_CODENAME}" \
      org.label-schama.usage="https://github.com/cbp44/docker_images/blob/master/dockerize/USAGE.md#${UBUNTU_CODENAME}" \
      org.label-schama.url="https://github.com/jwilder/dockerize" \
      org.label-schama.vcs-url="https://github.com/cbp44/docker_images"

# label-schame.org version used for labels
LABEL org.label-schema.schema-version="1.0.0-rc1"

# Copy dockerize into image from dockerize:base
COPY --from=dockerize /usr/local/bin/dockerize /usr/local/bin/dockerize

ENTRYPOINT ["dockerize"]
CMD ["--help"]
