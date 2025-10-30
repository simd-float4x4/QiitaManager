---
title: 【Next.js】ポート番号を指定して仮想サーバーを起動する
tags:
  - Next.js
private: false
updated_at: '2025-10-27T15:11:19+09:00'
id: 0f8befdfed6299338abd
organization_url_name: null
slide: false
ignorePublish: false
---
### 概要
* ボート番号を`3000`や`3001`から変更したい場合`npm run dev`に引数を設定することでポート番号を変更することが出来る。

### コマンド
```Shell
// ポート番号3334を指定して起動
$ npm run dev -p 3334
```

* 引数`-p`を指定することを忘れないこと。
