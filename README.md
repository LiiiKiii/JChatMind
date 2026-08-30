# JChatMind

JChatMind 是一个基于 Spring Boot + Spring AI 的 AI Agent 项目，包含后端服务、前端界面，以及一组本地初始化资源。

当前仓库主要用于本地开发和项目整理，目录中已经包含：

- 后端服务：`jchatmind/`
- 前端界面：`ui/`
- 示例与初始化资源：`examples/`、`jchatmind/bootstrap/`

## 项目能力

- Agent 基础对话
- 多轮会话管理
- 工具调用
- 知识库管理
- Markdown 文档解析
- 基于 `pgvector` 的向量检索
- SSE 实时消息推送

## 技术栈

- Java 17
- Spring Boot 3
- Spring AI
- MyBatis
- PostgreSQL
- pgvector
- React 19
- Vite
- Ant Design

## 目录结构

```text
JChatMind/
├── jchatmind/                # Spring Boot 后端
│   ├── bootstrap/            # 初始化 SQL 与知识库示例文档
│   ├── scripts/              # 本地辅助脚本
│   └── src/
├── ui/                       # React 前端
├── examples/                 # 其他示例资源
└── docs/                     # 本地文档
```

## 环境要求

启动前请先准备：

- Java 17 或更高版本
- Node.js 20 或更高版本
- PostgreSQL
- `pgvector` 扩展

如果你要使用知识库向量化与 RAG 检索，还需要：

- 本地 embedding 服务
- 当前代码默认使用 `http://localhost:11434`

## 后端启动

```bash
cd /Users/macbook/projects/JChatMind/jchatmind
./mvnw spring-boot:run
```

默认后端端口：

```text
http://localhost:8080
```

## 前端启动

```bash
cd /Users/macbook/projects/JChatMind/ui
npm install
npm run dev
```

默认前端地址：

```text
http://127.0.0.1:5173
```

前端当前默认请求后端：

```text
http://localhost:8080/api
```

## 数据库说明

后端当前使用 PostgreSQL 数据库 `jchatmind`。

核心表结构和示例资源已经收口到：

- [jchatmind/bootstrap/sql/jchatmind.sql](/Users/macbook/projects/JChatMind/jchatmind/bootstrap/sql/jchatmind.sql:1)
- [jchatmind/bootstrap/sql/eshop.sql](/Users/macbook/projects/JChatMind/jchatmind/bootstrap/sql/eshop.sql:1)
- [jchatmind/bootstrap/sql/eshop_data.sql](/Users/macbook/projects/JChatMind/jchatmind/bootstrap/sql/eshop_data.sql:1)
- [jchatmind/bootstrap/knowledge/eshop.md](/Users/macbook/projects/JChatMind/jchatmind/bootstrap/knowledge/eshop.md:1)

这些文件只是项目内资源，不会自动导入数据库。

如果你需要手动初始化：

```bash
cd /Users/macbook/projects/JChatMind/jchatmind
psql -d jchatmind -f bootstrap/sql/jchatmind.sql
psql -d jchatmind -f bootstrap/sql/eshop.sql
psql -d jchatmind -f bootstrap/sql/eshop_data.sql
```

## 配置说明

后端配置文件位于：

- [jchatmind/src/main/resources/application.yaml](/Users/macbook/projects/JChatMind/jchatmind/src/main/resources/application.yaml:1)

这个文件通常包含本机数据库、模型、邮件等配置。提交到远程仓库前，建议确认其中不包含敏感信息。

当前 `.gitignore` 已忽略：

- 根目录 `.idea/`
- macOS 生成文件
- `jchatmind/src/main/resources/application.yaml`

## 当前状态

截至 2026-08-30，这个仓库已经具备：

- 后端源码
- 前端源码
- 本地 bootstrap 资源
- Git 基础忽略规则

但你在实际使用时仍需要自己确认：

- 本机 PostgreSQL 是否已启动
- `jchatmind` 数据库是否存在
- 模型与 API key 是否可用
- 本地 embedding 服务是否已启动

## 常用命令

后端测试：

```bash
cd /Users/macbook/projects/JChatMind/jchatmind
./mvnw test
```

前端打包：

```bash
cd /Users/macbook/projects/JChatMind/ui
npm run build
```

查看 Git 状态：

```bash
cd /Users/macbook/projects/JChatMind
git status
```