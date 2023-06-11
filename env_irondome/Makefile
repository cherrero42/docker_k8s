all: up

up:
	docker compose -f  up ./docker-compose.yml

recreate:
	docker compose -f ./docker-compose.yml up --force-recreate --build

down:
	docker compose -f ./docker-compose.yml down
  
clean_volume:
	rm -rf /home/inter/*
  
clean : clean_volume
	docker image prune
  docker container prune
  docker volume prune
  docker network prune
  docker system prune

re: clean up

r : down re
