# curious-moon-docker

Created for HG Insights' internal [A Curious Moon](https://bigmachine.io/products/a-curious-moon/) book club.

## Requirements

- Docker (or Docker Desktop on macOS)
- PostgreSQL client
  - macOS: `brew install libpq && echo 'export PATH="/opt/homebrew/opt/libpq/bin:$PATH"' >> ~/.zshrc`
  - Debian/Ubuntu: `sudo apt-get install postgresql-client`
  - Windows: [download](http://postgresql.org/download/) and install

## Setup

### Download and extract data archive

```sh
curl -o data.zip '<data_url_from_book_club_notes>'
unzip data.zip 'curious_data/*'
```

## Usage

### Start Postgres

```sh
docker-compose up -d
```

### Connect to database

Choose _one_ of the following methods:

#### Native client

```sh
export $(cat .env)
psql enceladus
```

#### Container client

```sh
docker exec -it $(docker ps | grep cassini | awk '{print $1}') /usr/local/bin/psql enceladus
```

### Stop Postgres

```sh
docker-compose down
```
