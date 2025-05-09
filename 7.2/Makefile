
CMD-DOCKER-IMAGE-VENDOR = hhdev
CMD-DOCKER-IMAGE-NAME = ionic
CMD-DOCKER-IMAGE-TIER = 7.2-njs22-jvm21

build:
	docker build \
		-f ./Dockerfile \
		--progress=plain \
		--no-cache \
		--rm \
		-t ${CMD-DOCKER-IMAGE-VENDOR}/${CMD-DOCKER-IMAGE-NAME}:${CMD-DOCKER-IMAGE-TIER} . \
		> build.log 2>&1

clean:
	@docker rmi ${CMD-DOCKER-IMAGE-VENDOR}/${CMD-DOCKER-IMAGE-NAME}:${CMD-DOCKER-IMAGE-TIER}
	@docker builder prune --all --force

up:
	@docker run -d \
		--name ${CMD-DOCKER-IMAGE-VENDOR}_${CMD-DOCKER-IMAGE-NAME}_${CMD-DOCKER-IMAGE-TIER} \
		-t ${CMD-DOCKER-IMAGE-VENDOR}/${CMD-DOCKER-IMAGE-NAME}:${CMD-DOCKER-IMAGE-TIER}

down:
	@docker stop ${CMD-DOCKER-IMAGE-VENDOR}_${CMD-DOCKER-IMAGE-NAME}_${CMD-DOCKER-IMAGE-TIER}
	@docker rm ${CMD-DOCKER-IMAGE-VENDOR}_${CMD-DOCKER-IMAGE-NAME}_${CMD-DOCKER-IMAGE-TIER}

log:
	@docker logs -f ${CMD-DOCKER-IMAGE-VENDOR}_${CMD-DOCKER-IMAGE-NAME}_${CMD-DOCKER-IMAGE-TIER}

console:
	@docker exec -it --user developer ${CMD-DOCKER-IMAGE-VENDOR}_${CMD-DOCKER-IMAGE-NAME}_${CMD-DOCKER-IMAGE-TIER} /bin/bash

push:
	docker push ${CMD-DOCKER-IMAGE-VENDOR}/${CMD-DOCKER-IMAGE-NAME}:${CMD-DOCKER-IMAGE-TIER}
