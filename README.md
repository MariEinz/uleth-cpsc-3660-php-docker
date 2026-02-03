# Uleth CPSC 3660 — PHP + Docker (student repo)

Welcome! This repository provides a Docker-based PHP development environment used in CPSC 3660. The README below explains how to start and stop the environment, and how to access the running PHP instance.

## Quick overview

- Purpose: provides a local instance of mysql and php using Docker.
- PHP instance: available at http://localhost:80
- Typical workflow:
  1. Install Docker (and Docker Compose if needed).
  2. Go to the **.env** file and **add the same password** to both fields.
  3. From the repo folder run `docker compose up -d`.
  4. Visit http://localhost:80 in your browser.
  5. When finished, stop the environment with `docker compose down`.

---

## Prerequisites

- Git (optional, to clone the repo)
- A machine that supports Docker:
  - Windows 10/11 (recommended: WSL2 backend)
  - macOS (Intel or Apple Silicon)
  - Linux (Ubuntu, Fedora, etc.)

---

## Start the environment

From the root of this repository, run:

```
docker compose up -d
```

- This will build (if needed) and start the containers in detached mode.
- The `-d` runs containers in the background so you can keep using your terminal.

Verify containers are running:

```
docker ps
```

Access the application:

- Open your browser at: http://localhost:80
- The PHP instance is served at port 80 on localhost.

---

## Stop the environment

To stop and remove the containers started by Compose:

```
docker compose down
```

Additional useful commands:

- View logs (follow):
  ```
  docker compose logs -f
  ```
- Rebuild images (if you change Dockerfile or dependencies):
  ```
  docker compose up -d --build
  ```
- Run a shell inside a running container (example service name `php`; replace with actual service name if different):
  ```
  docker compose exec php bash
  ```
  (If the container uses `sh` only, use `sh` instead of `bash`.)

---

## Ports and where to look

- PHP / Web: http://localhost:80 (port 80)
- phpmyadmin is also included on http://localhost:8080 just in case

---

## Common issues & troubleshooting

- Port 80 is in use:
  - Find the process using port 80 and stop it, or change the port mapping in `docker-compose.yml`.
  - On Linux/macOS:
    ```
    sudo lsof -i :80
    ```
- Permission denied / can't connect to Docker on Linux:
  - Make sure you added your user to the `docker` group and re-logged in:
    ```
    sudo usermod -aG docker $USER
    ```
- `docker compose` not found but `docker-compose` is available:
  - Use `docker-compose up -d` as a fallback, or install the Compose plugin.
- Containers not starting or crash-looping:
  - Check logs:
    ```
    docker compose logs -f
    ```
  - Remove old volumes (careful, this removes persistent data):
    ```
    docker compose down -v
    ```

---

Good luck and happy coding!
