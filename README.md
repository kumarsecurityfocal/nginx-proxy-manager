**NGINX Proxy Manager with MariaDB on Docker**

This repository contains a Docker Compose configuration to set up **NGINX Proxy Manager (NPM)** with **MariaDB** on Ubuntu 24.04 LTS. It provides an easy way to manage reverse proxies with a user-friendly interface.
Features
- **NGINX Proxy Manager**: A simple, powerful interface for managing reverse proxies.
- **MariaDB**: Used as the database backend for storing configuration and data.
- Dockerized for quick and consistent deployment.
Prerequisites
Before starting, ensure you have the following installed on your Ubuntu system:
•	- **Docker**: Install Docker Engine.
•	- **Docker Compose**: For managing multi-container Docker applications.
Setup Instructions
Step 1: Clone the Repository
```bash
git clone https://github.com/your-username/nginx-proxy-manager-docker.git
cd nginx-proxy-manager-docker
```
Step 2: Configure Environment Variables
1. Copy the `.env.example` file to `.env`:
```bash
cp .env.example .env
```
2. Update the variables in the `.env` file:
```env
MARIADB_ROOT_PASSWORD=root_password
MARIADB_DATABASE=npm_db
MARIADB_USER=npm
MARIADB_PASSWORD=npm_password
DB_MYSQL_HOST=db
DB_MYSQL_PORT=3306
DB_MYSQL_NAME=npm_db
DB_MYSQL_USER=npm
DB_MYSQL_PASSWORD=npm_password
```
Step 3: Start the Containers
Use Docker Compose to start the application:
```bash
docker-compose up -d
```
Step 4: Access the NPM Web Interface
1. Open your browser and navigate to:
```
http://<your-server-ip>:81
```
2. Log in with the default credentials:
- **Email**: `admin@example.com`
- **Password**: `changeme`
3. Change the default email and password after logging in.
Directory Structure
```plaintext
nginx-proxy-manager-docker/
├── data/              # Persistent data for NPM
├── letsencrypt/       # SSL certificates
├── mariadb/           # MariaDB data
├── docker-compose.yml # Docker Compose configuration
├── .env               # Environment variables
└── README.md          # Project documentation
```
Managing the Application
Viewing Logs
To view logs for troubleshooting:
```bash
docker-compose logs -f
```
Restarting Services
To restart the containers:
```bash
docker-compose restart
```
Stopping Services
To stop the containers:
```bash
docker-compose down
```
Security Recommendations
1. **Firewall**: Enable and configure a firewall:
```bash
sudo ufw allow 80
sudo ufw allow 443
sudo ufw allow 22
sudo ufw enable
```
2. **Environment File**: Do not expose your `.env` file in public repositories. Add it to `.gitignore`:
```bash
echo ".env" >> .gitignore
```
Backup and Restore
- Backup the following directories for persistence:
  - `data/`
  - `letsencrypt/`
  - `mariadb/`
- Automate backups using a cron job or a cloud-based solution.
License
This project is licensed under the [MIT License](LICENSE).
Contributions
Contributions are welcome! Please fork the repository, create a feature branch, and submit a pull request.
Issues
If you encounter any issues, feel free to open an [issue](https://github.com/your-username/nginx-proxy-manager-docker/issues).
Acknowledgments
- [NGINX Proxy Manager](https://nginxproxymanager.com/)
- [MariaDB](https://mariadb.org/)
- [Docker](https://www.docker.com/)
