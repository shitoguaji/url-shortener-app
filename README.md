# URL Shortener App

一个用于 DevOps 综合项目的短链接服务。

## 功能

- 创建短链接
- 访问短码 302 重定向
- 记录点击
- 自定义短码
- 链接过期
- 管理 API

## 架构

```text
Client -> Ingress -> API (FastAPI) -> Redis / PostgreSQL
```

## 本地运行

```bash
cp .env.example .env
docker compose up -d --build
curl -X POST http://localhost:8000/api/v1/links \
  -H "Content-Type: application/json" \
  -d '{"url":"https://example.com"}'
```

## 测试

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -e ".[dev]"
pytest
```

## 目录结构

```text
app/            应用代码
tests/          测试
docs/adr/       架构决策记录
.github/        CI 工作流
Dockerfile      镜像构建
```

## 相关仓库

- `url-shortener-infra`：Terraform 基础设施
- `url-shortener-gitops`：K8s 清单与 Argo CD
