# BlueSpice

BlueSpice (MediaWiki-basierte Wiki-Software für Unternehmen) auf Basis des offiziellen `bluespice-deploy`-Stacks.

## Start

```bash
docker compose -f docker-compose.helper-service.yml -f docker-compose.secrets.yml -f docker-compose.main.yml -f docker-compose.persistent-data-services.yml -f docker-compose.stateless-services.yml -f docker-compose.proxy.yml up -d
```

## Umgebungsvariablen (`.env`)

| Variable | Beschreibung |
|---|---|
| `VERSION` | Version des Stacks |
| `EDITION` | Edition (`free`, `pro`, `farm`) |
| `BACKUP_HOUR` | Stunde für das automatische Backup |
| `WIKI_NAME` | Name des Wikis |
| `WIKI_LANG` | Standardsprache |
| `WIKI_PASSWORDSENDER` | Absenderadresse für System-Mails |
| `WIKI_EMERGENCYCONTACT` | Notfall-Kontaktadresse |
| `WIKI_HOST` | Hostname des Wikis |
| `WIKI_PORT` | Port des Wikis |
| `WIKI_PROTOCOL` | Protokoll (`http` oder `https`) |
| `WIKI_BASE_PATH` | Basispfad der Installation |
| `DB_USER` | Datenbank-Benutzer |
| `DB_PASS` | Passwort des Datenbank-Benutzers |
| `DB_ROOT_USER` | Root-Benutzer der Datenbank |
| `DB_ROOT_PASS` | Root-Passwort der Datenbank |
| `DB_HOST` | Hostname der Datenbank |
| `DB_NAME` | Name der Datenbank |
| `DB_PREFIX` | Tabellen-Präfix |
| `SMTP_HOST` | SMTP-Server |
| `SMTP_PORT` | SMTP-Port |
| `SMTP_USER` | SMTP-Benutzer |
| `SMTP_PASS` | SMTP-Passwort |
| `SMTP_ID_HOST` | Hostname für die SMTP-Identität |
| `ANTIVIRUS` | Virenscanner aktivieren |
| `LETSENCRYPT` | Let's-Encrypt-Zertifikate aktivieren |
| `CHAT` | Chat-Dienst aktivieren |
| `AI` | KI-Dienst aktivieren |
| `BLUESPICE_SERVICE_REPOSITORY` | Repository der Service-Images |
| `BLUESPICE_WIKI_IMAGE` | Verwendetes Wiki-Image |
| `UPGRADE_ACTION` | Kommando des Upgrade-Containers (`sleep 1` = kein Upgrade) |
| `INTERNAL_WIKI_SECRETKEY` | Secret des Wikis |
| `INTERNAL_WIKI_UPGRADEKEY` | Upgrade-Key des Wikis |
| `INTERNAL_SIMPLESAMLPHP_ADMIN_PASS` | Admin-Passwort von SimpleSAMLphp |
| `INTERNAL_SIMPLESAMLPHP_SECRET_SALT` | Salt von SimpleSAMLphp |
| `INTERNAL_SIMPLESAMLPHP_SESSION_API_TOKEN` | Session-API-Token von SimpleSAMLphp |
| `INTERNAL_CHAT_TOKEN` | Token zwischen Wiki und Chat |
| `INTERNAL_CHAT_WIKI_ACCESS_TOKEN` | Zugriffstoken zwischen Wiki und Chat |
| `INTERNAL_WIKI_TOKEN_AUTH_SALT` | Auth-Salt für Wire und Chat |
| `INTERNAL_WIRE_API_KEY` | API-Key zwischen Wiki und Wire |
| `CHAT_AI_CHAT_SERVICE_API_KEY` | API-Key zwischen Chat und KI |
