all: build push

default: build

build:
	docker build -t rbschange/php:5.4 -t rbschange/php:latest -t rbschange/php:apache-5.4 .

push:
	docker push rbschange/php:5.4
	docker push rbschange/php:apache-5.4
	docker push rbschange/php:latest

