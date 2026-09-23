# E-commerce API

一个基于 FastAPI 构建的电商后端 API 项目，主要实现用户认证、商品管理、购物车、订单及支付等核心业务功能。

项目采用异步编程方式构建 API，并结合 PostgreSQL、Redis、JWT 等技术，实现较完整的电商后端服务。

## 功能特性

* **用户认证**：基于 JWT 实现用户注册、登录及权限控制
* **商品管理**：支持商品的创建、查询、修改和删除
* **购物车管理**：支持商品添加、删除、数量修改及购物车金额计算
* **订单管理**：实现订单创建及订单相关数据处理
* **支付功能**：集成 Paystack 支付接口
* **数据校验**：使用 Pydantic 对请求参数和响应数据进行校验
* **数据库操作**：使用 SQLAlchemy ORM 操作 PostgreSQL 数据库
* **缓存与后台任务**：使用 Redis 实现缓存及后台任务处理
* **自动化测试**：使用 pytest 编写接口及业务逻辑测试
* **容器化部署**：提供 Docker 配置，支持容器化运行

## 技术栈

| 技术         | 用途             |
| ---------- | -------------- |
| FastAPI    | 构建 RESTful API |
| Python     | 后端开发           |
| Pydantic   | 数据校验与配置管理      |
| SQLAlchemy | ORM 数据库操作      |
| PostgreSQL | 关系型数据库         |
| Redis      | 缓存与后台任务        |
| JWT        | 用户认证与授权        |
| Paystack   | 支付接口           |
| pytest     | 自动化测试          |
| Alembic    | 数据库迁移          |
| Docker     | 容器化部署          |
| Poetry     | Python 依赖管理    |

## 项目结构

```text
ecommerce-api/
├── alembic/                # 数据库迁移
├── core/                   # 配置及核心功能
├── crud/                   # 数据库 CRUD 操作
├── api/                    # API 路由及接口
├── models/                 # SQLAlchemy 数据模型
├── schemas/                # Pydantic 数据模型
├── tests/                  # 自动化测试
├── task_queue/             # 后台任务
├── main.py                 # 应用程序入口
├── pyproject.toml          # 项目及依赖配置
├── Dockerfile              # Docker 配置
└── README.md
```

## 环境要求

* Python 3.11
* PostgreSQL
* Redis
* Docker（可选）
* Poetry

## 快速开始

### 1. 获取项目

```bash
git clone https://github.com/hui86306-hash/ecommerce-api.git
cd ecommerce-api
```

### 2. 安装依赖

本项目使用 Poetry 管理 Python 依赖：

```bash
poetry install --no-root
```

激活虚拟环境：

```bash
poetry run <command>
```

也可以直接使用：

```bash
poetry run <command>
```

### 3. 配置环境变量

在项目根目录创建 `.env` 文件。

可以复制项目中的 `.env.example` 作为配置模板，然后根据本地环境修改数据库、Redis、JWT 和支付相关配置。

> `.env` 文件仅用于本地开发，不应提交到 Git 仓库。

### 4. 数据库迁移

执行 Alembic 数据库迁移：

```bash
poetry run alembic upgrade head
```

### 5. 启动项目

```bash
poetry run uvicorn main:app --reload
```

启动后访问：

```text
http://localhost:8000
```

FastAPI 自动生成的接口文档：

```text
http://localhost:8000/docs
```

## API 测试

项目提供 Postman Collection，可导入 Postman 后测试 API 接口。

文件：

```text
ecommerce.postman_collection.json
```

也可以直接使用 FastAPI Swagger UI：

```text
http://localhost:8000/docs
```

## 运行测试

项目使用 pytest 进行自动化测试。

```bash
poetry run pytest
```

如果需要查看详细测试信息：

```bash
poetry run pytest -v
```

## Docker

构建镜像：

```bash
docker build -t ecommerce-api .
```

运行容器：

```bash
docker run --name ecommerce-api \
  -p 8000:8000 \
  --env-file .env \
  ecommerce-api
```

## 数据库迁移

项目使用 Alembic 管理数据库版本。

升级到最新版本：

```bash
poetry run alembic upgrade head
```

创建新的迁移：

```bash
poetry run alembic revision --autogenerate -m "update database"
```

## 项目说明

本项目用于学习和实践现代 Python Web 后端开发技术，重点涉及：

* RESTful API 设计
* FastAPI 异步接口开发
* JWT 身份认证
* SQLAlchemy ORM
* PostgreSQL 数据库设计
* Redis 缓存
* 数据库迁移
* 自动化测试
* Docker 容器化部署

## 开源协议

本项目基于 MIT License 开源。

如对项目进行二次开发或重新分发，请遵循原项目所采用的开源许可证及相关署名要求。
