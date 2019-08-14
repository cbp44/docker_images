.PHONY: build

build_date != date -u +"%Y-%m-%dT%H:%M:%SZ"
# base_built = true

build: base/Dockerfile bionic/Dockerfile xenial/Dockerfile
	docker build --force-rm --build-arg BUILD_DATE=${build_date} -t dockerize:base ./base
	docker build --force-rm --build-arg BUILD_DATE=${build_date} -t dockerize:xenial ./xenial
	docker build --force-rm --build-arg BUILD_DATE=${build_date} -t dockerize:bionic ./bionic
