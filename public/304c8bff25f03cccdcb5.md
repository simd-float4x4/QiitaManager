---
title: 【Swift/Realm】テーブルの全削除
tags:
  - Swift
  - Realm
  - SwiftUI
private: false
updated_at: '2025-10-26T21:04:25+09:00'
id: 304c8bff25f03cccdcb5
organization_url_name: null
slide: false
ignorePublish: false
---
### 概要
* Realmのテーブルを削除する。
* リリース時、実装時に増えすぎたマイグレーションを整理して1からやり直したい際があると思われるため。

### 手順
1-1. アプリを削除する。データも削除する。
1-2. `@main`修飾子が付与されているファイルで一番最初に下記のコードを実装する。
```Swift
let realm = try! Realm()
try! realm.write {
    realm.deleteAll()
}
```
1-3. migration系のコードを実装している場合は、必ず`SchemaVersion`を`1`にしておくことを忘れない。
```Swift
schemaVersion: 1
```
1-4. migration関連のコードを全てコメントアウトしておく。
1-5. ビルド
1-6. delete系のコードを消しておく（あるいは開発時のみに有効にしておくこと）
