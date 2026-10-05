# XWiki

XWiki (Java-basierte Wiki-Plattform) mit MariaDB.

## Start

```bash
docker compose up -d
```

## Umgebungsvariablen (`.env`)

| Variable | Beschreibung |
|---|---|
| `XWIKI_VERSION` | Version des XWiki-Images |
| `DB_USER` | Datenbank-Benutzer |
| `DB_PASSWORD` | Passwort des Datenbank-Benutzers |
| `DB_DATABASE` | Name der Datenbank |
| `MYSQL_ROOT_PASSWORD` | Root-Passwort der MariaDB |
