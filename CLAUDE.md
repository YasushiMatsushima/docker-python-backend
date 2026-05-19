# docker-python-backend — Claude 開発ガイド

## プロジェクト概要

Docker + FastAPI によるバックエンド API 開発環境。

- **バックエンド:** FastAPI (Python 3.12) — ポート 8080
- **DB:** PostgreSQL 13 — ポート 5432
- **GitHub:** https://github.com/YasushiMatsushima/docker-python-backend

---

## ディレクトリ構成

```
/
├── app/
│   ├── main.py          # エントリポイント・エンドポイント定義
│   └── .env             # シークレット（Git管理外）
├── .devcontainer/
│   └── devcontainer.json
├── .claude/
│   ├── settings.json
│   └── commands/
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
└── CLAUDE.md
```

---

## ローカル開発

### サーバー起動確認

| サービス | URL | 確認方法 |
|---|---|---|
| FastAPI | http://localhost:8080 | `curl http://localhost:8080/` |
| Swagger UI | http://localhost:8080/docs | ブラウザで確認 |
| Scalar UI | http://localhost:8080/scalar | ブラウザで確認 |

### Docker 操作

```bash
# 起動
docker compose up -d

# 停止
docker compose down

# ログ確認
docker compose logs -f

# イメージ再ビルド（requirements.txt 変更後）
docker compose up --build -d
```

### venv（VSCode の補完用）

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

> 実際の起動は Docker で行う。venv は VSCode の補完を効かせるために使う。

---

## よく使うカスタムコマンド

| コマンド | 説明 |
|---|---|
| `/commit` | 変更をコミット |
| `/api-check` | 主要エンドポイントの動作確認 |
