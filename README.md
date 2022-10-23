# WordPress Docker

The project creates three Docker containers for quickly spinning up a development environment to work on WordPress using the latest version of MySQL and WordPress.

## Requirements

- Docker
- Git Bash (*If using Windows*)

## Configuration

- (Optional) Update the following credentials if preferred:

```yml
##  docker-compose.yml

## db service environmental variables
      - MYSQL_ROOT_PASSWORD=wordpress
      - MYSQL_DATABASE=wordpress
      - MYSQL_USER=wordpress
      - MYSQL_PASSWORD=wordpress

## wordpress service environmental variables
      - WORDPRESS_DB_HOST=db:3306
      - WORDPRESS_DB_USER=wordpress
      - WORDPRESS_DB_PASSWORD=wordpress
```

## Run

**Build containers**

- Open Git Bash and execute the following command:

```bash
docker-compose up -d
```

**(Optional) Re-run build command**

If you encounter issues with network latency or timeouts, simply run the following command to tear down ALL docker container, images, and volumes.

**WARNING** All docker containers, images, and volumes will be deleted

```bash
./cleanup.sh
docker-compose up -d
```

**Run the wizard**

- Start WordPress by opening a browser and navigate to `http://localhost`
- Go through the normal WordPress setup wizard

**(Optional) Database login**

If you want to examine the database from a browser, do the following:

- Open the browser and navigate to `http://localhost:8001`
- When prompted, provide the username and password defined with `MYSQL_USER` and `MYSQL_PASSWORD` above

## Stop and Restart

**Stop a running stack**

If the stack is currently working up and running, execute the following to stop stack without destroying anything.

```bash
docker compose stop
```

*WARNING* This will take a few minutes to bring down completely and the volumes remain running but that's fine.

(Optional) If the containers do not stop after a few minutes, you could execute a kill command.

```bash
docker compose kill
```

**Restart a stack**

To restart the stack without recreating it, run the following:

```bash
docker compose start
```
