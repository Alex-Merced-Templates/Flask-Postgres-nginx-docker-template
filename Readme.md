# Using this Template
**[TEMPLATE BASED ON THIS ARTICLE](https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/)**

## Environmental Variables Needed

#### /.env.dev

```
FLASK_APP=project/__init__.py
FLASK_ENV=development
DATABASE_URL=postgresql://hello_flask:hello_flask@db:5432/hello_flask_dev
APP_FOLDER=/home/app/web
```

#### /.env.prod

```
FLASK_APP=project/__init__.py
FLASK_ENV=production
DATABASE_URL=postgresql://hello_flask:hello_flask@db:5432/hello_flask_prod
SQL_HOST=db
SQL_PORT=5432
DATABASE=postgres
APP_FOLDER=/home/app/web
```

#### /.env.prod.db

```
POSTGRES_USER=hello_flask
POSTGRES_PASSWORD=hello_flask
POSTGRES_DB=hello_flask_prod
```

#### /services/web/config.py

```
import os


basedir = os.path.abspath(os.path.dirname(__file__))


class Config(object):
    SQLALCHEMY_DATABASE_URI = os.getenv("DATABASE_URL", "sqlite://")
    SQLALCHEMY_TRACK_MODIFICATIONS = False
```

## Commands

- Build Docker Compose File `docker-compose build`

- Run Docker Compose `docker-compose up -d`

- Take down compose with volumes `docker-compose down -v`

- Run and Build `docker-compose up -d --build`

- Run a command `docker-compose exec <service> <command>`

- check if volume exists `docker volume inspect <networkname>_<volumename>`

- Remove a volume `docker-compose rm <servicename>`

- Make script executable `chmod +x SCRIPT.sh`

- Docker Compose with custom file `$ docker-compose -f <FILE.yml> up -d --build`
