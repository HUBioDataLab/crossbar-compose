ENV_FLAGS = --env-file ./.env --env-file ../env/site.env --env-file ../env/sensitive/oidc.env --env-file ../env/sensitive/auth.env

up:
	sudo docker compose $(ENV_FLAGS) up --remove-orphans -d

down:
	sudo docker compose $(ENV_FLAGS) down

logs:
	sudo docker compose $(ENV_FLAGS) logs -f

update:
	sudo docker compose $(ENV_FLAGS) pull
	sudo docker compose $(ENV_FLAGS) up --remove-orphans -d --force-recreate
