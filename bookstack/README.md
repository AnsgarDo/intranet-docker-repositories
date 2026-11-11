# BookStack

BookStack (Wiki-/Dokumentations-Software) auf Basis des Community-Images
[`solidnerd/bookstack`](https://hub.docker.com/r/solidnerd/bookstack/) mit MariaDB.
Es wird kein eigenes Dockerfile benötigt, das Image wird direkt referenziert.

## Start

```bash
docker compose up -d
```

Danach ist BookStack unter <http://localhost:8082> erreichbar.
Erster Login: `admin@admin.com` / `password` (bitte sofort ändern).

## Umgebungsvariablen (`.env`)

Die Datei `.env` muss **vor** dem ersten Start im Ordner `bookstack/` liegen
(sie ist per `.gitignore` ausgeschlossen und daher nicht im Repository).

```
APP_KEY=<32 Zeichen>
MARIADB_ROOT_PASSWORD=<Root-Passwort der MariaDB>
DB_DATABASE=bookstack
DB_USERNAME=bookstack
DB_PASSWORD=<Passwort des Datenbank-Benutzers>
APP_URL=http://localhost:8082
```

Fehlt die Datei bzw. einzelne Werte, startet Docker Compose zwar, meldet aber:

```
WARN[0000] The "DB_PASSWORD" variable is not set. Defaulting to a blank string.
WARN[0000] The "MARIADB_ROOT_PASSWORD" variable is not set. Defaulting to a blank string.
WARN[0000] The "MARIADB_ROOT_PASSWORD" variable is not set. Defaulting to a blank string.
WARN[0000] The "DB_PASSWORD" variable is not set. Defaulting to a blank string.
WARN[0000] The "APP_KEY" variable is not set. Defaulting to a blank string.
```

In diesem Fall schlägt der Start der Container fehl (MariaDB ohne Passwort,
BookStack ohne `APP_KEY`). `.env` anlegen und `docker compose up -d` erneut ausführen.
Prüfen lässt sich die Konfiguration ohne Start mit `docker compose config --quiet`
(Exit-Code `0` = alle Variablen aufgelöst).

| Variable | Beschreibung |
|---|---|
| `APP_KEY` | Schlüssel für die Verschlüsselung, 32 Zeichen. Einmalig erzeugen mit `docker run --rm solidnerd/bookstack:26.9.2 php artisan key:generate --show` und dauerhaft beibehalten |
| `APP_URL` | Basis-URL ohne abschließenden Slash, inkl. Port (z. B. `https://wiki.example.com`) |
| `MARIADB_ROOT_PASSWORD` | Root-Passwort der MariaDB |
| `DB_DATABASE` | Name der Datenbank |
| `DB_USERNAME` | Datenbank-Benutzer |
| `DB_PASSWORD` | Passwort des Datenbank-Benutzers |

`DB_HOST` ist fest auf `db:3306` gesetzt (Host und Port werden kombiniert).

## Persistente Daten

| Volume | Pfad im Container |
|---|---|
| `bookstack-db-data` | `/var/lib/mysql` |
| `bookstack-uploads` | `/var/www/bookstack/public/uploads` |
| `bookstack-storage-uploads` | `/var/www/bookstack/storage/uploads` |

## Links

- [Docker Hub](https://hub.docker.com/r/solidnerd/bookstack/)
- [GitHub Repository](https://github.com/solidnerd/docker-bookstack)
- [BookStack Dokumentation](https://www.bookstackapp.com/docs/)
