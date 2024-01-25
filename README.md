
# Challenge Application

This repository contains a simple web application with two main components: an API written in PHP Laravel and a client developed using Nuxt.js.

## Table of Contents

- [Requirements](#requirements)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Setting Up CentOS Environment](#setting-up-centos-environment)
  - [Setting Up the Application](#setting-up-the-application)
  - [Running the Application](#running-the-application)
- [Docker Compose](#docker-compose)
- [CI/CD](#cicd)
- [Folder Structure](#folder-structure)

## Requirements

- Docker
- Docker Compose
- Git
- CentOS environment

## Getting Started

### Prerequisites

Make sure you have Docker, Docker Compose, and Git installed on your machine. Additionally, ensure you have access to a CentOS environment.

- [Docker Installation Guide](https://docs.docker.com/get-docker/)
- [Docker Compose Installation Guide](https://docs.docker.com/compose/install/)
- [Git Installation Guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

### Setting Up CentOS Environment

1. Install Docker and Docker Compose on CentOS:

    ```bash
    sudo yum install -y docker docker-compose
    ```

2. Start and enable the Docker service:

    ```bash
    sudo systemctl start docker
    sudo systemctl enable docker
    ```

3. Clone the repository to your CentOS machine:

    ```bash
    git clone https://github.com/your-username/challenge.git
    ```

4. Navigate to the project directory:

    ```bash
    cd challenge
    ```

### Setting Up the Application

#### API

1. Navigate to the API directory:

    ```bash
    cd api
    ```
2. Set appropriate permissions for the storage directory. For example, you can use the following command:

    ```bash
    chmod -R 775 storage
    ```

3. Return to the project root directory:

    ```bash
    cd ..
    ```

#### Client

1. Navigate to the client directory:

    ```bash
    cd client
    ```
2. Return to the project root directory:

    ```bash
    cd ..
    ```

### Running the Application

1. Run Docker Compose to start the MySQL database, PHP Laravel API, Nuxt.js client, and Nginx proxy:

    ```bash
    docker-compose up -d
    ```

2. Access the application in your web browser at [http://localhost](http://localhost:3000) or [https://localhost](https://localhost) if using the self-signed certificate.

## Docker Compose

A Docker Compose file is included for easy deployment of the entire application stack.

```bash
docker-compose up -d
```
This command will start the MySQL database, PHP Laravel API, Nuxt.js client, and Nginx proxy.

### CI/CD
The project includes GitHub Actions workflows for continuous integration and continuous deployment. Images for the API and client are built and pushed to Docker Hub on every push to the main branch.

## Folder Structure

Here is the basic structure of the project:

```plaintext
challenge/                 # Root directory of the project
│
├── api/                   # PHP Laravel API
│   ├── app/               # Laravel application code
│   ├── database/          # Database migrations and seeds
│   ├── public/            # Publicly accessible files
│   ├── resources/         # Views, assets, and localization files
│   ├── routes/            # API route definitions
│   ├── tests/             # PHPUnit tests
│   ├── .env.example       # Example environment file
│   ├── Dockerfile         # Dockerfile for building the API image
│   └── apache.conf        # VHOST for Apache
│
├── client/                # Nuxt.js Client
│   ├── app.vue            # Main Vue.js application component
│   ├── .env               # Environment configuration file
│   ├── nuxt.config.ts     # Nuxt.js configuration file in TypeScript
│   ├── package.json       # Node.js package configuration
│   ├── server/            # Server-side code or configuration (if applicable)
│   ├── public/            # Publicly accessible files and assets
│   ├── Dockerfile         # Dockerfile for building the client image
│   └── tsconfig.json      # TypeScript configuration file
│
├── nginx/                 # Nginx Configuration
│   ├── default.conf       # Nginx server configuration
│   ├── nginx.crt          # SSL certificate file (generated in bonus challenge)
│   ├── nginx.key          # SSL private key file (generated in bonus challenge)
│   └── ...                # Other Nginx-related files
│
├── .github/               # GitHub Actions workflows
│   ├── workflows/         # Workflows for CI/CD
│   └── ...                # Other GitHub Actions files
│
├── .gitignore             # Gitignore file to specify ignored files
├── docker-compose.yml     # Docker Compose configuration file
├── README.md              # Project README
└── ...                    # Other project files and documentation

