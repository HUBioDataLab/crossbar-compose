ENV_FLAGS = --env-file ../env/site.env --env-file ../../env/site.env

up:
	docker compose $(ENV_FLAGS) up --remove-orphans -d

down:
	docker compose $(ENV_FLAGS) down

logs:
	docker compose $(ENV_FLAGS) logs -f

update:
	docker compose $(ENV_FLAGS) pull
	docker compose $(ENV_FLAGS) up --remove-orphans -d --force-recreate
