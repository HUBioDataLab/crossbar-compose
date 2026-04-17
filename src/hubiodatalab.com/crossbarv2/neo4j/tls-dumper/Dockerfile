FROM ldez/traefik-certs-dumper:v2.8.3

RUN apk add --no-cache jq bash

COPY ./entrypoint.bash .
COPY ./neo4j-hook.bash .
RUN chmod +x ./entrypoint.bash ./neo4j-hook.bash

ENTRYPOINT ./entrypoint.bash
