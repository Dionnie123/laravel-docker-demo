# Develop Laravel Project inside Docker for Beginners

By: Mark Dionnie Bulingit

## Setup Laravel environment on Windows

Credits to ther Author, very comprehensive topic about dockerizing laravel.

https://medium.com/@chewysalmon/laravel-docker-development-setup-an-updated-guide-72842dfe8bdf

## Keynotes

Laravel uses Composer to install dependencies, we use composer-image from dockerhub to install composer inside our project container and delete it after -pretty convenient.

```powershell
docker run --rm -v ${pwd}:/app composer install
```

Now we have Composer but only inside the container, we will start ou laravel commands with e.g

```powershell
docker-compose exec app php artisan key:generate
```

## Composer dependency & PHP version error

_composer detected issues in your platform: Your Composer dependencies require a PHP version ">= 8.2.0". You are running 8.0.30._

Go to package.json

```powershell
   "config": {
        "platform-check": false
    },
```

```powershell
docker run --rm -v ${pwd}:/app composer dump-autoload
```

## Frequently used commands

Note: Make sure you're using Powershell terminal and Docker Desktop is running.

```bash
docker-compose down ; docker run --rm -v ${pwd}:/app composer install ; docker run --rm -v ${pwd}:/app composer install ; docker-compose up
```

-   Stops and Delete containers
-   Install dependecies
-   Start and run containers

# Check Files

-   docker-compose.yaml
-   web.dockerfile
-   app.dockerfile
-   vhost.conf
