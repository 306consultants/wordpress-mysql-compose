
# WordPress + MySQL Docker Compose Setup

This repository provides a **Docker Compose file** to quickly set up a local development environment for WordPress and MySQL. It is designed for developers and designers to test ideas, build sites, or stage projects before migrating to a live instance.

**Note:** While this setup can be used for self-hosting, it is primarily intended as a temporary solution for development purposes.

---

## Getting Started

### Step 1: Install Docker and Docker Compose

To use this repository, you’ll need Docker and Docker Compose. Follow these steps:

#### Download Docker Desktop (includes Docker Compose):
1. Go to the [Docker Desktop download page](https://www.docker.com/products/docker-desktop/).
2. Download and install Docker Desktop for your operating system (Windows, macOS, or Linux).
3. Follow the installation instructions provided by Docker.

#### Verify Installation:
1. Open a terminal or command prompt.
2. Run the following commands to ensure Docker and Docker Compose are installed:
   ```bash
   docker --version
   docker compose version
   ```
   Both commands should return version information.

---

### Step 2: Clone This Repository

1. Open your terminal or command prompt.
2. Run the following command to clone this repository:
   ```bash
   git clone https://github.com/306consultants/wordpress-mysql-compose.git
   ```
3. Navigate into the repository folder:
   ```bash
   cd your-repo-name
   ```

---

### Step 3: Start the Containers

Run the following command to start the WordPress and MySQL containers:
```bash
docker compose up -d
```
This command will:
- Download the necessary images (WordPress and MySQL) if they are not already on your system.
- Start the containers in detached mode (`-d`).

#### Access Your Local WordPress Site:
1. Open a web browser.
2. Navigate to `http://localhost:8080`.
3. You should see the WordPress setup page.

---

## Managing Multiple Instances

If you want to run more than one instance of WordPress:
1. Edit the `docker-compose.yml` file before starting a new instance.
2. Change the `ports` section under the WordPress service:
   ```yaml
   ports:
     - "8081:80" # Example for a second instance
   ```
3. Save the file and run:
   ```bash
   docker compose up -d
   ```

**Important:** Make sure not to run multiple containers using the same port (e.g., `8080:80`). If you don't edit the port, start only one instance at a time.

---

## Stopping the Containers

To stop the running containers:
```bash
docker compose down
```

This will stop and remove the containers, but your data (WordPress content and MySQL database) will be preserved in the Docker volumes defined in the `docker-compose.yml` file.

---

## Removing Everything

If you want to completely remove the containers and data:
1. Stop the containers:
   ```bash
   docker compose down
   ```
2. Remove the associated volumes:
   ```bash
   docker volume rm your-repo-name_db_data your-repo-name_wordpress_data
   ```

---

## Troubleshooting

- **Can’t access WordPress?**
  Ensure Docker Desktop is running and check for errors in the terminal.

- **Port conflict?**
  Make sure no other services or containers are using port `8080`. Change the port in the `docker-compose.yml` file if needed.

---

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvement, feel free to open an issue or submit a pull request.

---

Happy developing!
