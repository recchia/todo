# TODO API
A todo task list


This api was develop on top of the following tools.

* [Api Plarform](https://api-platform.com) - REST and GraphQL framework to build modern API-driven projects
* [Nginx](https://nginx.org/en/) - Nginx [engine x] is an HTTP and reverse proxy server.
* [PHP-FPM](https://php-fpm.org/) - Alternative PHP FastCGI implementation with additional features useful for sites of any size.
* [MYSQL](https://www.mysql.com/) - MySQL is the world's most popular open source database.
* [Redis](https://redis.io/) - Redis is an open source, in-memory data structure store.
* [Docker](https://www.docker.com/) - Docker is an open platform for developers and sysadmins to build, ship, and run distributed applications.

### Requirements

  - Docker 17.12.1-ce
  - Docker Compose 1.19.0
  
### Setup, Build & Run

In order to getting the api working you need to execute the next commands.

```sh
$ git clone https://github.com/recchia/todo.git
$ cd todo
$ docker-compose up -d
$ docker exec -ti todo_php bash
$ composer install --prefer-dist
```

Next you should browse [http://127.0.0.1:8080](http://127.0.0.1:8080) to see the app running and click on document link to see examples and try the API.
