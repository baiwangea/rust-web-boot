# rust-web-starter

[English](./README.md) | [中文](./README.zh-CN.md)

## Introduction

This is a Rust web starter template, designed to provide a solid foundation for building modern, high-performance web applications. It comes pre-configured with a popular and powerful set of libraries.

## Features

- **Web Framework**: [Axum](https://github.com/tokio-rs/axum) for building robust and scalable web services.
- **Asynchronous Runtime**: [Tokio](https://tokio.rs/) as the foundation for asynchronous I/O.
- **Database ORM**: [SeaORM](https://www.sea-ql.org/SeaORM/) for safe and efficient interaction with PostgreSQL.
- **Authentication**: JWT-based authentication using [jsonwebtoken](https://crates.io/crates/jsonwebtoken) and password hashing with [bcrypt](https://crates.io/crates/bcrypt).
- **Configuration Management**: Flexible configuration using [config](https://crates.io/crates/config) from `application.yaml`.
- **Validation**: Request validation with [validator](https://crates.io/crates/validator) and [axum-valid](https://crates.io/crates/axum-valid).
- **Logging**: Structured and configurable logging with [tracing](https://crates.io/crates/tracing).
- **Embedded Frontend**: The frontend (located in the `web` directory) is embedded into the application binary using [rust-embed](https://crates.io/crates/rust-embed).

## Getting Started

### Prerequisites

- [Rust](https://www.rust-lang.org/tools/install)
- [cross](https://github.com/cross-rs/cross) for cross-compilation (`cargo install cross`)
- [PostgreSQL](https://www.postgresql.org/download/)

### 1. Database Setup

1.  Make sure your PostgreSQL server is running.
2.  Update the database connection details in `application.yaml` to match your environment.
3.  Create the database and tables by executing the `schema.sql` file.

    ```sql
    -- Example using psql
    psql -U your_username -d your_database -f schema.sql
    ```

### 2. Application Configuration

Adjust the settings in `application.yaml` as needed, such as the server port.

### 3. Build and Run

You can build and run the application in several ways:

**Development:**

```bash
cargo run
```

**Production (Linux):**

The `build.sh` script provides a convenient way to build a release binary for Linux.

```bash
./build.sh
```

The executable will be located at `target/x86_64-unknown-linux-musl/release/web-starter`.

## Project Structure

```
.
├── Cargo.toml         # Rust dependencies and project metadata
├── Cargo.lock         # Exact versions of dependencies
├── README.md          # This file
├── README.zh-CN.md    # Chinese README
├── application.yaml   # Application configuration
├── build.sh           # Build script for production
├── schema.sql         # Database schema
├── src                # Backend source code
│   └── main.rs
└── web                # Frontend source code (embedded at compile time)
```
