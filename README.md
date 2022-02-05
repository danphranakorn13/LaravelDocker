### PHP Laravel Environment (Docker)

## Required

- Docker version 20.10.12 or later
- Docker Compose version v2.2.3 or later

## Services

- NGINX:stable-alpine
- php:7.4-fpm (Laravel)
- mysql:8
- phpmyadmin:latest (5 April 2022)

## How to install

1. Clone this project && cd to laravel folder
```bash
git clone 
cd socialLogin/laravel
```
>Create empty folder
```bash
mkdir laravel mysql
```

2. Create **.env** file 
```bash
mv .env.example .env
vi .env
```
>**.env** <br>
```bash
APP_NAME=**<YOUR_APP_NAME>** <br>
MYSQL_ROOT_PASSWORD=**<YOUR_MYSQL_ROOT_PASSWORD>**
```

3. Run docker-compose
go back to socialLogin path
```bash
cd ..
```

>Run docker-compose
```bash
docker-compose up -d 
```

4. Exec to app container (Laravel container) and create laravel project
>Exec to app container
```bash
docker-compose exec app bash
```

>Create laravel project
```bash
:/var/www$ composer create-project laravel/laravel --prefer-dist .
```

>Out of the app container
```bash
:/var/www$ exit
``` 

>Connect database
**.env**
```bash
APP_URL=http://localhost:8000

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=<YOUR_APP_NAME>_db
DB_USERNAME=<YOUR_APP_NAME>_user
DB_PASSWORD=password
``` 

>***note how to migrate**
```bash
docker-compose exec app php artisan migrate
``` 

5. Go to your web browser <br> 
- Laravel <a>http://localhost:8000/</a>
- phpmyadmin <a>http://localhost:8081/</a>
