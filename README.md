# SQL Assist

A SQL assistant that turns natural-language questions into SQL, runs queries against SQLite databases, and explains the results in plain language.

## Table of Contents

- [Description](#description)
- [Installation](#installation)
- [Usage](#usage)
- [Features](#features)
- [Configuration](#configuration)
- [License](#license)

## Description

SQL Assist is a full-stack TypeScript application with a React frontend and an Express backend. The backend uses LangChain and Together AI to inspect SQLite table schemas, generate SQL, execute it, and return a natural-language response.

The repository also provides Docker configuration for running the backend together with SQLite.

## Project Structure

``` sql-assistant/
├── client/           # Frontend application
├── server/           # Backend API and services
└── .github/          # GitHub workflows and configurations
```

## Installation

### Prerequisites

- Node.js 18 or later
- npm
- Docker and Docker Compose, if using containers

### Install and run locally

1. Clone the repository:

```bash
git clone https://github.com/efe-osa/SQL-Assist.git
cd SQL-Assist
```

2. Install and start the backend:

```bash
cd server
npm install
npm run dev
```

The backend starts on port `3001` by default.

3. In another terminal, install and start the frontend:

```bash
cd client
npm install
npm run dev
```

4. Configure the frontend and backend as described in [Configuration](#configuration), then open the URL displayed by Vite.

## Usage

### Generate SQL

Enter a natural-language description in the interface and select **Generate SQL Query**. SQL Assist uses the current SQLite schema to produce a query.

### Ask the database

Enter a question and select **Ask the database**. SQL Assist will:

1. Generate a SQL query.
2. Execute it against the default SQLite database.
3. Send the question, SQL, schema, and result to the language model.
4. Display a natural-language answer.

### Add a database

Select **Add Database using URL**, enter a database URL and name, and the backend will download the SQLite file and register it as an additional database connection.

## Features

- Natural-language SQL query generation
- SQL execution against SQLite
- Natural-language answers based on database results
- Schema-aware prompts through LangChain
- Runtime SQLite database registration
- React and Vite frontend
- Express API with security and rate-limiting middleware
- Docker support for the backend and SQLite
- GitHub Actions workflows for frontend and backend checks
- MIT license

## Configuration

Keep credentials and local settings out of source control.

1. Create a local server configuration from `server/env.example` and fill in the required private values.
2. Configure the frontend with the locally reachable backend API URL.
3. Add API credentials and database settings only through local configuration or deployment secrets.

Do not commit configuration files containing credentials.

The backend Docker setup reads an environment file and expects the frontend and backend to be able to communicate over the configured network and API URL.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
