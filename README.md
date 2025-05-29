# crossbar-compose

Check out the `.env.example` file and replace the placeholders with your actual values.
Please also consider the warning about secret management.

To run the project:

```bash
git clone https://github.com/HUBioDataLab/crossbar-compose.git
cd crossbar-compose

# Edit the .env file accordingly
cp .env.example .env

docker compose build
docker compose up -d
```

## Environment Variables

```env
ACME_JSON_PATH=/letsencrypt/hubiodatalab.com.json
MAIN_DOMAIN=crossbarv2.hubiodatalab.com
NEO4J_DOMAIN=neo4j.crossbarv2.hubiodatalab.com

NEO4J_USERNAME=neo4j
NEO4J_URI=bolt://neo4j:7687
NEO4J_DATABASE_NAME=neo4j
API_PORT=4000

# Values below should be considered secrets. It's better not to keep them in plain text.
# You can either keep them in GitHub secrets, or opt for secret management tools like HashiCorp Vault.
# It's your responsibility to handle this.

# An example secret key for CSRF protection. You should replace this with a your own secret key.
# This is just a placeholder and should not be used in production.
# Generate one with "openssl rand -hex 32"
CSRF_SECRET_KEY=a4d29f713c6bd04fa46921352ec12f6f318cd66c0877d98ba1ad02fa8a582318

NEO4J_AUTH="neo4j/password"
MY_NEO4J_PASSWORD="password"

OPENAI_API_KEY=sk-*
GEMINI_API_KEY=AI*
ANTHROPIC_API_KEY=sk-ant*
GROQ_API_KEY=gsk_*
NVIDIA_API_KEY=nvapi-*
OPENROUTER_API_KEY=sk-*
```