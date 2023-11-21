# glead-and-position
Changing account for glead and changing users for position
Изменение активности акккаунта и установка бесплатности для аккаунта glead
Изменение юзеров системы графиков для position


## Ports

Ports used in the project:
| Software | Port |
|-------------- | -------------- |
| **nginx** | 8080 |
| **phpmyadmin** | 8081 |
| **mariadb** | 3306 |
| **php** | 9000 |
| **xdebug** | 9001 |
| **redis** | 6379 |

## Use

1. Заготовка для докера под лару 8:

   ```sh
   git clone https://github.com/supermavster/docker-laravel-8.git
   ```

2. Inside the folder `docker-laravel-8` and Generate your own `.env` to docker compose with the next command:

   ```sh
   cp .env.example .env
   ```

3. You need **Create** or **Put** your laravel project in the folder source; to create follow the next instructions [Here](README.md).

4. Build the project whit the next commands:

   ```sh
   docker-compose up --build
   ```

---

## Remember

The configuration of the database **must be the same on both sides** .

```dotenv
# .env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=db_name
DB_USERNAME=db_user
DB_PASSWORD=db_password
DB_ROOT_PASSWORD=secret
```

```dotenv
# lead-pos-admin/.env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=db_name
DB_USERNAME=db_user
DB_PASSWORD=db_password
```

The only change is the `DB_HOST` in the `lead-pos-admin/.env` where is called to the container of `mysql`:

```dotenv
# lead-pos-admin/.env
DB_HOST=mysql
```

---

## Special Cases

To Down and remove the volumes we use the next command:

```sh
docker-compose down -v
```

Update Composer:

```sh
docker-compose run --rm composer update
```

Run compiler (Webpack.mix.js) or Show the view compiler in node:

```sh
docker-compose run --rm npm run dev
```

Run all migrations:

```sh
docker-compose run --rm artisan migrate
```

## Remember

The configuration of the database **must be the same on both sides** .

```dotenv
# .env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=db_name
DB_USERNAME=db_user
DB_PASSWORD=db_password
DB_ROOT_PASSWORD=secret
```

```dotenv
# lead-pos-admin/.env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=db_name
DB_USERNAME=db_user
DB_PASSWORD=db_password
```

The only change is the `DB_HOST` in the `lead-pos-admin/.env` where is called to the container of `mysql`:

```dotenv
# lead-pos-admin/.env
DB_HOST=mysql
```

---

## Help

A little help to create the project:

### Make a new Project

```sh
docker-compose run --rm composer create-project laravel/laravel .
```

### Copy Environment

```sh
cp .env.example .env
```

---

### Install Libraries from Composer

```sh
docker-compose run --rm composer install
```

### Install Libraries from Node

```sh
docker-compose run --rm npm install
```

### Clear/Clean the project

```sh
docker-compose run --rm artisan clear:data
docker-compose run --rm artisan cache:clear
docker-compose run --rm artisan view:clear
docker-compose run --rm artisan route:clear
docker-compose run --rm artisan clear-compiled
docker-compose run --rm artisan config:cache
docker-compose run --rm artisan storage:link
```

### Generate Keys

```sh
docker-compose run --rm artisan key:generate
```

### Run migrations

```sh
docker-compose run --rm artisan migrate --seed
```

### Run Passport (Optional)

```sh
docker-compose run --rm artisan passport:install
```
