#
#  Author: Hari Sekhon
#  Date: 2017-09-13 14:47:23 +0200 (Wed, 13 Sep 2017)
#
#  vim:ts=4:sts=4:sw=4:noet
#
#  https://github.com/harisekhon/Dockerfiles
#
#  If you're using my code you're welcome to connect with me on LinkedIn and optionally send me feedback to help improve or steer this or other code I publish
#
#  https://www.linkedin.com/in/harisekhon
#

REPO := harisekhon/presto-dev

include ../Makefile.in

TAG := $(shell ./get_presto_versions.sh | head -n1)

MAP_PORTS := 8080

.PHONY: build
build:
	docker build -t $(REPO):$(TAG) --build-arg PRESTO_DEVELOPMENT_VERSION=$(TAG) .

.PHONY: history
history:
	./build_historic_versions.sh

.PHONY: history
history-push:
	PUSH=1 ./build_historic_versions.sh

.PHONY: build-versions
build-versions: build history
	:

.PHONY: build-push-versions
build-push-versions: build push history-push
	:

.PHONY: nocache
nocache:
	docker build -t $(REPO):$(TAG) --build-arg PRESTO_DEVELOPMENT_VERSION=$(TAG) --no-cache .
