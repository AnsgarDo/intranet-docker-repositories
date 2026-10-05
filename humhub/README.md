# HumHub

HumHub (Social-Network-Software für Intranets) auf Basis des offiziellen Docker-Images.

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
| `SERVER_NAME` | Adresse, auf der der Webserver lauscht |
| `HUMHUB_DEBUG` | Debug-Modus aktivieren |
| `HUMHUB_CONFIG__COMPONENTS__DB__DSN` | Datenbank-DSN |
| `HUMHUB_CONFIG__COMPONENTS__DB__USERNAME` | Datenbank-Benutzer |
| `HUMHUB_CONFIG__COMPONENTS__DB__PASSWORD` | Datenbank-Passwort |
| `HUMHUB_CONFIG__CONTROLLER_MAP__INSTALLER` | Registriert den Installer-CLI-Befehl für die unbeaufsichtigte Installation |
| `HUMHUB_ADMIN_USER` | Benutzername des HumHub-Administrators |
| `HUMHUB_ADMIN_PASSWORD` | Passwort des HumHub-Administrators |
| `HUMHUB_ADMIN_EMAIL` | E-Mail-Adresse des HumHub-Administrators |
