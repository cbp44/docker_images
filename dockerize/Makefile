.PHONY: all bionic xenial push

all: bionic xenial

bionic: bionic/Dockerfile
	docker build --force-rm -t dockerize:bionic ./bionic
	docker tag dockerize:bionic cbp44/dockerize:latest

xenial: xenial/Dockerfile
	docker build --force-rm -t dockerize:xenial ./xenial

push:
	docker tag dockerize:bionic cbp44/dockerize:latest
	docker push cbp44/dockerize:latest
