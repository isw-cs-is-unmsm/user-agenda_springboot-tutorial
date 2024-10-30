
# Docker and Docker Compose Installation for Windows Users

To set up this environment, you'll need Docker and Docker Compose installed on your Windows system.

### Install Docker Desktop

1. Download Docker Desktop from the official Docker website: [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop).
2. Run the installer and follow the installation steps.
3. After installation, open Docker Desktop and ensure it is running.

### Install Docker Compose

Docker Compose comes pre-installed with Docker Desktop. If you need to update Docker Compose, follow these steps:

1. Open a terminal (PowerShell or Command Prompt).
2. Check the version of Docker Compose by running:

   ```bash
   docker-compose --version
   ```

If Docker Compose is installed, you should see the version number. If not, please follow the [Docker Compose installation documentation](https://docs.docker.com/compose/install/).

---

# Docker Compose Setup for MySQL and phpMyAdmin

This Docker Compose configuration file defines two main services: a MySQL database and phpMyAdmin for managing the database through a web interface.

## Services

### 1. MySQL Database (`mysql-db`)

- **Image**: `mysql:latest`  
  Uses the latest version of MySQL. You can replace it with `mariadb:latest` if you prefer MariaDB.

- **Container Name**: `mysql-db`  
  The name given to the MySQL container.

- **Environment Variables**:
  - `MYSQL_DATABASE`: Creates a database named `user_agenda_db` upon container initialization.
  - `MYSQL_ROOT_PASSWORD`: Sets the root user password (`rootpassword`). Ensure this is secure in a production environment.
  - `MYSQL_USER`: Creates an additional user named `user`.
  - `MYSQL_PASSWORD`: Sets the password for the `user` (`userpassword`).

- **Ports**: `3306:3306`  
  Exposes the MySQL database on port 3306 so it can be accessed from `localhost:3306`.

- **Volumes**:
  - `mysql_data:/var/lib/mysql`  
    Stores MySQL data in a Docker-managed volume (`mysql_data`) to persist database data outside the container, preventing data loss when the container restarts.

### 2. phpMyAdmin (`phpmyadmin`)

- **Image**: `phpmyadmin/phpmyadmin:latest`  
  Uses the latest phpMyAdmin image to provide a web-based interface to manage MySQL.

- **Container Name**: `phpmyadmin`  
  The name given to the phpMyAdmin container.

- **Environment Variables**:
  - `PMA_HOST`: Specifies `mysql-db` as the host, linking phpMyAdmin to the MySQL container.
  - `MYSQL_ROOT_PASSWORD`: Provides the root password to access MySQL as root.

- **Ports**: `8080:80`  
  Exposes phpMyAdmin on `localhost:8080`, allowing access via [http://localhost:8080](http://localhost:8080).

- **Dependencies**:
  - `depends_on`: Ensures that the `mysql-db` service starts before phpMyAdmin.

## Volumes

- **mysql_data**:
  - This volume is named `mysql_data` and is managed by Docker locally.
  - It persists MySQL data by mapping it to `/var/lib/mysql` in the MySQL container.

## Usage

To start the services, use the following command in the directory containing this `docker-compose.yml`:

```bash
docker-compose up -d
```

This command will start both the MySQL and phpMyAdmin containers in detached mode.

Access phpMyAdmin at [http://localhost:8080](http://localhost:8080) and log in with the MySQL credentials specified.

