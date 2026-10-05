# Open Intranet

Open Intranet (Drupal-Distribution für Unternehmens-Intranets) als Docker-Stack.

## Start

```bash
docker compose up -d
```

## Umgebungsvariablen (`.env`)

| Variable | Beschreibung |
|---|---|
| `MARIADB_ROOT_PASSWORD` | Root-Passwort der MariaDB |
| `MARIADB_DATABASE` | Name der Datenbank |
| `MARIADB_USER` | Datenbank-Benutzer |
| `MARIADB_PASSWORD` | Passwort des Datenbank-Benutzers |
| `DRUPAL_ADMIN_USER` | Benutzername des Drupal-Administrators |
| `DRUPAL_ADMIN_PASSWORD` | Passwort des Drupal-Administrators |
| `DRUPAL_ADMIN_EMAIL` | E-Mail-Adresse des Drupal-Administrators |
