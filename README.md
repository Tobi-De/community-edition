# Plausible Community Edition

### Prerequisites

- **[Docker](https://docs.docker.com/engine/install/)** and **[Docker Compose](https://docs.docker.com/compose/install/)** must be installed on your machine.
- **CPU:** Must support **SSE 4.2** instruction set or higher (required by ClickHouse).
- **Memory:** At least **2 GB of RAM** is recommended for running ClickHouse efficiently.
- **Storage:** Adequate disk space to store your ClickHouse and PostgreSQL databases, depending on your expected data volume.

### Quick start

To set up Plausible Community Edition quickly, follow these steps:

1. Clone this repository:

    ```console
    $ git clone -b v2.1.2 --single-branch https://github.com/plausible/community-edition plausible-ce
    Cloning into 'plausible-ce'...
    remote: Enumerating objects: 13, done.
    remote: Counting objects: 100% (10/10), done.
    remote: Compressing objects: 100% (9/9), done.
    remote: Total 13 (delta 0), reused 7 (delta 0), pack-reused 3 (from 1)
    Receiving objects: 100% (13/13), done.

    $ cd plausible-ce

    $ ls -1
    README.md
    clickhouse/
    compose.yml
    ```

1. Create and configure your [environment file:](https://docs.docker.com/compose/environment-variables/)

    ```console
    $ touch .env
    
    $ echo "HTTP_PORT=8080" >> .env
    $ echo "HTTPS_PORT=8443" >> .env
    $ echo "BASE_URL=https://plausible.example.com:8443" >> .env
    $ echo "SECRET_KEY_BASE=$(docker run -ti --rm ghcr.io/plausible/community-edition:v2.1.2 openssl rand -base64 48)" >> .env
    
    $ cat .env
    HTTP_PORT=8080
    HTTPS_PORT=8443
    BASE_URL=https://plausible.example.com:8443
    SECRET_KEY_BASE=As0fZsJlUpuFYSthRjT5Yflg/NlxkFKPRro72xMLXF8yInZ60s6xGGXYVqml+XN1
    ```

1. Start the services with Docker Compose:

    ```console
    $ docker compose up -d
    ```

### Next steps

For more information on installation, upgrades, extra configuration, and available integrations please see our [wiki.](https://github.com/plausible/community-edition/wiki)
