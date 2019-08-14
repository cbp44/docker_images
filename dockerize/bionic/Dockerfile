# Use curl buildpack-deps image to get curl installed for us to download dockerize from GitHub
FROM buildpack-deps:bionic-curl as install


# Version of Dockerize to install
ARG DOCKERIZE_VERSION=v0.6.1
# The md5sum for the v0.6.1 tar.gz archive from GitHub (calculated by me on August 14, 2019)
ARG DOCKERIZE_ARCHIVE_MD5SUM=5c1b3d9a7d9341e23e0b8bdf2a288387

# Install Dockerize to /usr/local/bin/dockerize
RUN set -xe; \
    TAR_FILE=dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz; \
    curl --progress-bar -L -o /tmp/$TAR_FILE https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/$TAR_FILE; \
    [ $DOCKERIZE_ARCHIVE_MD5SUM = `md5sum /tmp/$TAR_FILE | cut -d ' ' -f 1` ] \
      && echo "\nSUCCESS: The md5sum of $TAR_FILE matches previously calculated value.\n" \
      || (echo "\nERROR: The md5sum of $TAR_FILE does not match previously calculated value of $DOCKERIZE_ARCHIVE_MD5SUM\n" && exit 1); \
    tar -C /usr/local/bin -xzvf /tmp/$TAR_FILE; \
    chmod +x /usr/local/bin/dockerize; \
    rm -f /tmp/$TAR_FILE

# Start fresh with ubuntu and copy dockerize into it
FROM ubuntu:bionic as base

LABEL maintainer="Chris Preusch"

# Info about this Dockerfile and the associated Docker image
LABEL org.label-schama.name="dockerize:bionic" \
      org.label-schama.version="1.0" \
      org.label-schama.description="An ubuntu:bionic image with dockerize pre-installed and set to the ENTRYPOINT." \
      org.label-schama.license="MIT" \
      org.label-schama.docker.cmd="docker run --rm cbp44/dockerize:bionic" \
      org.label-schama.usage="https://github.com/cbp44/docker_images/dockerize/USAGE.md" \
      org.label-schama.url="https://github.com/jwilder/dockerize" \
      org.label-schama.vcs-url="https://github.com/cbp44/docker_images"

# label-schame.org version used for labels
LABEL org.label-schema.schema-version="1.0.0-rc1"

# The date and time the public Docker image was built
ARG BUILD_DATE
LABEL org.label-schama.build-date=$BUILD_DATE


COPY --from=install /usr/local/bin/dockerize /usr/local/bin/dockerize

ENTRYPOINT ["dockerize"]
CMD ["--help"]
