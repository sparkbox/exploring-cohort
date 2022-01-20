# Consistent Environment


## Docker
Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications.


### Terms
  `Image 📸`  <!-- .element: class="fragment" -->
  
  `Container 👟`  <!-- .element: class="fragment" -->
  
  `Volume 💾` <!-- .element: class="fragment" -->


### Important Files 📝
  * Dockerfile
  * Docker-compose.yml


### Dockerfile
```
FROM php:8.0-apache-bullseye

# install the PHP extensions we need
RUN  apt-get update; && apt-get install -y;

COPY --from=composer:2.0 /usr/bin/composer /usr/local/bin/
RUN apt-get update && apt-get install -y git

COPY composer.json /opt/drupal
COPY composer.lock /opt/drupal
```


### php:zts-buster Dockerfile
```
...

ENTRYPOINT ["docker-php-entrypoint"]
CMD ["php" "-a"]
```


### docker-compose.yml
```
version: "3.7"

services:
  web:
    build: .
    container_name: example-web
    depends_on:
      - db
    ports:
      - 8081:80
    volumes:
      - .:var/www/html
...


```
...
  db:
    image: mysql:8.0
    container_name: example-db
    env_file: .env
    ports:
      - 3307:3306
    volumes:
      - db-data:/var/lib/mysql

volumes:
  db-data:
```


<iframe style="border:none" width="800" height="450" src="https://whimsical.com/embed/S198j6UbPoayaV9r4tdf2b"></iframe>


## Requirements

All app code should be running inside of Docker. Your web server should be running on port 80 inside of the Docker container, and available on 8000 from your local machine.
