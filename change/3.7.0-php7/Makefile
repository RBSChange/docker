all: build push

default: build

build:
	docker build -t rbschange/change:3.7.0 -t rbschange/change:3.7 -t rbschange/change:php7 -t rbschange/change:3.7.0-php7 .

push:
	docker push rbschange/change:3.7
	docker push rbschange/change:3.7.0
	docker push rbschange/change:php7
	docker push rbschange/change:3.7.0-php7
