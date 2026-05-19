# API 動作確認

バックエンド API の主要エンドポイントを一括チェックして、レスポンスを報告してください。

## 手順

以下の Python コードで各エンドポイントを確認する:

```python
import urllib.request, json

BASE = "http://localhost:8080"
endpoints = [
    ("GET", "/"),
    ("GET", "/health"),
    ("GET", "/shipment"),
]

for method, path in endpoints:
    try:
        req = urllib.request.Request(f"{BASE}{path}", method=method)
        with urllib.request.urlopen(req, timeout=5) as r:
            body = json.loads(r.read().decode())
            print(f"✓ {method} {path} → {r.status} {body}")
    except Exception as e:
        print(f"✗ {method} {path} → ERROR: {e}")
```

引数でエンドポイントが指定された場合はそれを優先: $ARGUMENTS
