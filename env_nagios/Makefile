.PHONY: all
all: 
	up

.PHONY: ip_show
ip_show:
	docker network inspect nagios_nagios -f '{{ range .Containers }}{{ .Name }} {{ .IPv4Address }}{{ " \n"}}{{ end }}' 

.PHONY: up
up:
	docker compose -f ./docker-compose.yml up -d

.PHONY: recreate
recreate:
	docker compose -f ./docker-compose.yml up --force-recreate --build	

.PHONY: down
down:
	docker compose -f ./docker-compose.yml down

.PHONY: re
re:
	clean up

.PHONY: r
r:
	down re

.PHONY: exec
exec:
	docker exec -it nagios  /bin/bash
