# Ready for deploy Django + Postgres + Gunicorn + Nginx

Using docker compose to run 3 services: Django with gunicorn, Postgresql and Nginx. To run a dev build execute:
```
$ docker-compose --build -d
# For migrations
$ docker-compose exec web python manage.py flush --no-input
$ docker-compose exec web python manage.py migrate
```
To run a prod build execute:
```
$ docker-compose -f docker-compose.prod.yml up -d --build
$ docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput
$ docker-compose -f docker-compose.prod.yml exec web python manage.py collectstatic --no-input --clear
```
dev server run on 10000 port, prod nginx run on 1337
