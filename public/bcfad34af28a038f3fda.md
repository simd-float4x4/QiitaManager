---
title: pip install django psycopg2-binaryした時に発生したエラーあれこれ
tags:
  - Python
  - Windows
private: false
updated_at: '2025-10-10T12:07:24+09:00'
id: bcfad34af28a038f3fda
organization_url_name: null
slide: false
ignorePublish: false
---

### 環境
・Windows

### 仮想環境に入れてない
```
$ .\venv\Scripts\Activate.ps1
Python
```

【解決策】
・[設定]>[アプリ]>[アプリの詳細設定]>[アプリの実行エイリアス]を開く
・アプリインストーラの項目を参照
・python.exe, python3.exeをオフにする

------

### pg_configに関するエラー

```
$ Error: pg_config executable not found.
```

【解決策】
・PostgreSQLをダウンロード

------

### django.core.exceptions.ImproperlyConfigured: Error loading psycopg2 or psycopg module
```
$ python manage.py migrate
(略)
$ django.core.exceptions.ImproperlyConfigured: Error loading psycopg2 or psycopg module
```

【解決策】
・pip install django psycopg2-binaryでダウンロードしていたが下記に変更
・python -m pip install "psycopg[binary]"
