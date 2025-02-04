# CodeChain Indexer [![Build Status](https://travis-ci.org/CodeChain-io/codechain-indexer.svg?branch=master)](https://travis-ci.org/CodeChain-io/codechain-indexer) [![codecov](https://codecov.io/gh/CodeChain-io/codechain-indexer/branch/master/graph/badge.svg)](https://codecov.io/gh/Codechain-io/codechain-indexer)

A blockchain data indexing tool for CodeChain

## Table of Contents

- [Install](https://github.com/CodeChain-io/codechain-indexer#install)
- [Before start](https://github.com/CodeChain-io/codechain-indexer#before-start)
- [Run](https://github.com/CodeChain-io/codechain-indexer#run)

## Install

#### Requirements

The software dependencies required to install and run CodeChain-indexer are:

- Latest version of the [CodeChain](https://github.com/CodeChain-io/codechain)
- PostgreSQL [`v11.*`](https://www.postgresql.org/download/)
- Nodejs higher than version 10

#### Download

Download CodeChain-indexer code from the GitHub repository

```
git clone git@github.com:kodebox-io/codechain-indexer.git
cd codechain-indexer
```

#### Install packages

Use yarn package manager to install packages

```
yarn install
```

## Before start

#### Dependency

- Get CodeChain ready with the CodeChain RPC server
- Get PostgreSQL database ready for indexing block data

#### Create the database and user on the PostgreSQL

##### Mac

```
# Download postgresql with Homebrew
brew install postgresql
brew services start postgresql

# Create users and databases
psql postgres -f create_user_and_db.sql

# Create the schema of the database
yarn run migrate
```

##### Ubuntu

```
# Download postgresql
sudo apt install postgresql postgresql-contrib

# Create users and databases
sudo -u postgres psql -f create_user_and_db.sql

# Create tables
yarn migrate
```

## Run (for development)

```
yarn run start

# You can change the host of CodeChain and DB host on the config/dev.json
```

## Run (for production)

```
yarn build
NODE_ENV=production node ./build/index.js

# You can change the host of CodeChain and DB host on the config/production.json
```

## Test

```
# Create the test database
NODE_ENV=test yarn run migrate

# Start testing
yarn run test
```

## API document

```
NODE_ENV=dev yarn run start

# Swagger UI is running at "http://host:port/api-docs/"
```

## Tools

#### Delete all database data

```
yarn run reset
```
