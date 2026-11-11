# BlueSpice

BlueSpice (MediaWiki-basierte Wiki-Software für Unternehmen) auf Basis des offiziellen `bluespice-deploy`-Stacks.

## Start

```bash
docker compose -f docker-compose.helper-service.yml -f docker-compose.secrets.yml -f docker-compose.main.yml -f docker-compose.persistent-data-services.yml -f docker-compose.stateless-services.yml -f docker-compose.proxy.yml up -d
```

Konfiguration über `.env`.
