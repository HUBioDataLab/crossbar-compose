# crossbar-compose

Check out the `.env` files and replace the placeholders with your actual values.
Necessary information is given inside the corresponding `.env` files.
Please also consider the warning about secret management.

To run the project:

```bash
git clone https://github.com/HUBioDataLab/crossbar-compose.git

docker network create proxy

docker volume create letsencrypt
docker volume create neo4j-certificates

cd crossbar-compose/src
cd traefik && make up && cd ..

cd hubiodatalab.com
cd auth && make up && cd ..

cd crossbarv2
cd index && make up && cd ..
cd neo4j && make up && cd ..
cd apollo && make up && cd ..
cd llm && make up && cd ..
```

## Secrets

It's better not to keep them in plain text, or at least with loose permissions.
You can either keep them in GitHub secrets, or opt for secret management tools like HashiCorp Vault.
It's your responsibility to handle this.