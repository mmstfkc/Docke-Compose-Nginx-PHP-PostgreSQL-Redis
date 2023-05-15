# Postgres Redis Nginx Laravel docker-compose system

## Setup
```bash
  cp .env.example .env
```


Create Your nginx congif file in the nginx/sites-enabled. <br>
You can take the default.conf file as an example.<br>
All you have to do is add <b> /var/www/project-name/public </b> to root.

Up to system
```bash
    docker-compose up -d
```

After filling your env information in the project with the .env file information we created at the beginning, you need to update the required fields as follows.

```
    DB_HOST=my-postgres
    REDIS_HOST=my-redis
```