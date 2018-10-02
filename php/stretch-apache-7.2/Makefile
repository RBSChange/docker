all: build push

default: build

build:
	docker build -t rbschange/php:7 -t rbschange/php:7.2 -t rbschange/php:apache-7.2 .

push:
	docker push rbschange/php:7
	docker push rbschange/php:7.2
	docker push rbschange/php:apache-7.2
