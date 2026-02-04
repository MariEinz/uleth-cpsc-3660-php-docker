# Uleth CPSC 3660 — PHP, SQL + Docker

Welcome! This repository provides a Docker-based PHP development environment used in CPSC 3660. The README below explains how to start and stop the environment, and how to access the running PHP instance.

## Description

- Purpose: provides a local instance of mysql and php using Docker.
- PHP instance: available at http://localhost:80
- Typical workflow:
  1. Install Docker (and Docker Compose if needed).
  2. Go to the **.env** file and **add the same password** to both fields.
  3. From the repo folder run `docker compose up -d`.
  4. Visit http://localhost:80 in your browser.
  5. When finished, stop the environment with `docker compose down`.


The docker compose file will create a directory for your mysql DB in mysql_data. This will be mounted to the docker container to allow persistence. The php files in src are mounted to the php container again to allow for persistence and immediate reflection of updates to the php code.
## Getting Started

### Dependencies

- Git (optional, to clone the repo)
- A machine that supports Docker:
  - Windows 10/11 (recommended: WSL2 backend)
  - macOS (Intel or Apple Silicon)
  - Linux (Ubuntu, Fedora, etc.)

### Installing

- Docker install instructions can be found on the [official website](https://www.docker.com/get-started/)

1. Make sure docker and docker compose are installed and running
2. Clone this repo do a location on your computer
3. Run the following command in the *root folder* of the project
4. Go to the *.env* file and update both password spots with the *same password*
```
docker compose build
```

### Running the container

To run the container ensure docker is running then simply type the following command in the *root folder* 
```
docker compose up -d
```

### Stopping the container

To stop the container use the following command in the *root folder*
```
docker compose down
```

### Testing status

To double check if the container is running you can navigate to http://localhost:80 this page will tell you if the connection to mysql is working and also allow you to make sure the php instance is working.

