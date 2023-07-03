# MHM - Setup Enviroment(Quick Guide)

### 1. Clone repository in your local

```
git clone git@github.com:framgia/mhm-dd-management.git
```

_note: use ssh when you clone_

### 2. Build the docker container

```
docker-compose up -d --build
```

### 3. Create .env file.

```
cp sys_app/.env.example sys_app/.env
docker-compose exec app composer install
docker-compose exec app php artisan key:generate
```

### 4. Add Database Credentials

update the `DB_` variables part. To add the mysql credentials pleaser refer from
`docker-compose.yml`.

```
DB_CONNECTION=mysql
DB_HOST=database
DB_PORT=3306
DB_DATABASE=<placeholder>
DB_USERNAME=<placeholder>
DB_PASSWORD=<placeholder>
```

After save, run

```
docker-compose exec app php artisan optimize:clear
docker-compose exec app php artisan migrate
```

### 5. Visit it the application in browser

```
http://localhost:8080
```