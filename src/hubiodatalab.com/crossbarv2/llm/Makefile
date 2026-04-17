INSTANCES := main staging
FREE_INSTANCES := free

ALL_INSTANCES := $(INSTANCES) $(FREE_INSTANCES)

# 2. YOUR BASE LAYERS (Shared across all instances)
# These are the files you mentioned in your prompt
BASE_FLAGS := --env-file ../env/site.env \
              --env-file ../../env/site.env \
              --env-file ../env/neo4j.env \
			  --env-file ../env/sensitive/api-keys/gemini.env \
			  --env-file ../env/sensitive/api-keys/openai.env

# Default instance if none provided
INS ?= main

# Add the instance env file to the end of the flags
INS_FLAGS := --env-file .env.$(INS) \
			 --env-file ../env/sensitive/llm-$(INS).env \
			 --project-name llm-$(INS)


ifneq ($(filter $(INS),$(FREE_INSTANCES)),)
    EXTRA_LAYER := --env-file ../env/sensitive/api-keys/anthropic.env \
				   --env-file ../env/sensitive/api-keys/gemini.env \
				   --env-file ../env/sensitive/api-keys/groq.env \
				   --env-file ../env/sensitive/api-keys/nvidia.env \
				   --env-file ../env/sensitive/api-keys/openai.env \
				   --env-file ../env/sensitive/api-keys/openrouter.env
else
    EXTRA_LAYER :=
endif

ALL_FLAGS := $(BASE_FLAGS) $(EXTRA_LAYER) $(INS_FLAGS)

.PHONY: all up-all build-all down-all up down logs update

all: up-all

up-all:
	@for ins in $(ALL_INSTANCES); do \
		$(MAKE) up INS=$$ins; \
	done

down-all:
	@for ins in $(ALL_INSTANCES); do \
		$(MAKE) down INS=$$ins; \
	done

update-all:
	@for ins in $(ALL_INSTANCES); do \
		$(MAKE) update INS=$$ins; \
	done


up:
	sudo docker compose $(ALL_FLAGS) build
	sudo docker compose $(ALL_FLAGS) up --remove-orphans -d

down:
	sudo docker compose $(ALL_FLAGS) down

logs:
	sudo docker compose $(ALL_FLAGS) logs -f

update:
	sudo docker compose $(ALL_FLAGS) build --no-cache
	sudo docker compose $(ALL_FLAGS) up --remove-orphans -d --no-deps
