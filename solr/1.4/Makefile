all: build push

default: build

build:
	docker build -t rbschange/solr:1.4 -t rbschange/solr:latest .

push:
	docker push rbschange/solr

