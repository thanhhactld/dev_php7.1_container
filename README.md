# dev_php7.1_container
Container for dev php7.1 project

## Getting Started:
- Install docker engine, docker-compose
- Build Image: 
set image tag from .env file
```
TAG=-1.0.0
DOCKER_REGISTRY=haido/php7.1-dev
```

Build docker image
```
docker-compose build
```

Run docker image:
```
docker-compose up
```

Config app source:
```xml=
Listen 8080
<VirtualHost *:8080>
    DocumentRoot "/app/public" # config serve static content
    Alias   /api "/app/web_service/web" # config web api path
    <Directory />
            Options Indexes FollowSymLinks MultiViews
            Options FollowSymLinks
            AllowOverride None
            Require all granted
    </Directory>
    <Directory /app>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride All
            Order allow,deny
            allow from all
            Require all granted
    </Directory>
</VirtualHost>
```