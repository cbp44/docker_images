.PHONY: all bionic xenial

all: bionic xenial

bionic: bionic/Dockerfile
	docker build --force-rm -t dockerize:bionic ./bionic

xenial: xenial/Dockerfile
	docker build --force-rm -t dockerize:xenial ./xenial
