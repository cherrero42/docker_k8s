.PHONY: all
all: up

.PHONY: up
up:
	docker compose -f  up ./docker-compose.yml

.PHONY: recreate
recreate:
	docker compose -f ./docker-compose.yml up --force-recreate --build

.PHONY: down
down:
	docker compose -f ./docker-compose.yml down

.PHONY: clean_volume
clean_volume:
	rm -rf /home/inter/*
  
.PHONY: clean
clean : clean_volume
	docker image prune
  docker container prune
  docker volume prune
  docker network prune
  docker system prune

.PHONY: re
re: clean up

.PHONY: r
r : down re
