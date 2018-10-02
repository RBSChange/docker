all: build push

default: build

build:
	docker build -t rbschange/change:3.6 -t rbschange/change:3.6.9 -t rbschange/change:3.6.9-php5 -t rbschange/change:latest .

push:
	docker push rbschange/change:3.6
	docker push rbschange/change:3.6.9
	docker push rbschange/change:3.6.9-php5
	docker push rbschange/change:latest
