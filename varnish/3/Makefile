all: build push

default: build

build:
	docker build -t rbschange/varnish:3 -t rbschange/varnish:latest .

push:
	docker push rbschange/varnish

