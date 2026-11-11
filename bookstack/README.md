# BookStack

BookStack mit MariaDB (`solidnerd/bookstack`).

```bash
docker compose up -d
```

<http://localhost:8082> — Login `admin@admin.com` / `password`.

## `.env`

```
APP_KEY=<32 Zeichen>
MARIADB_ROOT_PASSWORD=<Passwort>
DB_DATABASE=bookstack
DB_USERNAME=bookstack
DB_PASSWORD=<Passwort>
APP_URL=http://localhost:8082
```

`APP_KEY` erzeugen: `docker run --rm solidnerd/bookstack:26.9.2 php artisan key:generate --show`


