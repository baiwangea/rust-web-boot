# rust-web-starter

[English](./README.md) | [中文](./README.zh-CN.md)

## 介绍

这是一个 Rust web 项目启动模板，旨在为构建现代化、高性能的 Web 应用程序提供坚实的基础。它预先配置了一套流行且功能强大的库。

## 特性

- **Web 框架**: 使用 [Axum](https://github.com/tokio-rs/axum) 构建健壮且可扩展的 Web 服务。
- **异步运行时**: 使用 [Tokio](https://tokio.rs/) 作为异步 I/O 的基础。
- **数据库 ORM**: 使用 [SeaORM](https://www.sea-ql.org/SeaORM/) 与 PostgreSQL 进行安全高效的交互。
- **认证**: 基于 JWT 的认证，使用 [jsonwebtoken](https://crates.io/crates/jsonwebtoken) 和 [bcrypt](https://crates.io/crates/bcrypt) 进行密码哈希。
- **配置管理**: 使用 [config](https://crates.io/crates/config) 从 `application.yaml` 进行灵活的配置。
- **验证**: 使用 [validator](https://crates.io/crates/validator) 和 [axum-valid](https://crates.io/crates/axum-valid) 进行请求验证。
- **日志**: 使用 [tracing](https://crates.io/crates/tracing) 进行结构化和可配置的日志记录。
- **嵌入式前端**: 前端代码（位于 `web` 目录）在编译时使用 [rust-embed](https://crates.io/crates/rust-embed) 嵌入到应用程序二进制文件中。

## 如何开始

### 环境准备

- [Rust](https://www.rust-lang.org/tools/install)
- [cross](https://github.com/cross-rs/cross) 用于交叉编译 (`cargo install cross`)
- [PostgreSQL](https://www.postgresql.org/download/)

### 1. 数据库设置

1.  确保您的 PostgreSQL 服务器正在运行。
2.  更新 `application.yaml` 中的数据库连接详细信息以匹配您的环境。
3.  通过执行 `schema.sql` 文件创建数据库和表。

    ```sql
    -- 使用 psql 的示例
    psql -U 你的用户名 -d 你的数据库 -f schema.sql
    ```

### 2. 应用配置

根据需要调整 `application.yaml` 中的设置，例如服务器端口。

### 3. 构建和运行

您可以通过多种方式构建和运行应用程序：

**开发环境:**

```bash
cargo run
```

**生产环境 (Linux):**

`build.sh` 脚本提供了一种为 Linux 构建发布二进制文件的便捷方法。

```bash
./build.sh
```

可执行文件将位于 `target/x86_64-unknown-linux-musl/release/web-starter`。

## 项目结构

```
.
├── Cargo.toml         # Rust 依赖和项目元数据
├── Cargo.lock         # 依赖的精确版本
├── README.md          # 英文 README
├── README.zh-CN.md    # 中文 README
├── application.yaml   # 应用配置
├── build.sh           # 生产环境构建脚本
├── schema.sql         # 数据库结构
├── src                # 后端源代码
│   └── main.rs
└── web                # 前端源代码 (编译时嵌入)
```
