# laravel-docker
Laravel Project on Docker

You will need these installed on your system.

- Docker
- Docker Compose


Clone the repository.

Go to the project directory and run the command 

```bash
docker-compose up --build
```

Get access to the containers bash with testuser

```bash
docker exec -ti -u testuser laravel-docker_app_1 bash
```

To get details explanation on how to setup/create your own Laravel project on Docker you can read this [article on medium]()
