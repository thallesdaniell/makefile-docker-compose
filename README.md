# Makefile custom for docker-compose

```
include .env

default: start

start: down up

up:
	@docker-compose up --build -d

down:
  ifeq ($(shell docker ps -q | wc -l),0)
		@echo 'no docker started...'
  else
		@docker kill $(shell docker ps -q)
  endif

bash: #ex: container_name: ${APP_NAME}_postgres //run: make bash shell=postgres
	@docker exec -it ${APP_NAME}_${shell} bash
```

if you have a lot of projects, always start with make
