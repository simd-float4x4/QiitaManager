---
title: 【Swift】UserDefaults(Bool型)の初回起動時のnil対策がいらなかった話
tags:
  - Swift
private: false
updated_at: '2025-10-28T22:25:27+09:00'
id: 54ce62b60ef5ab4bdae1
organization_url_name: null
slide: false
ignorePublish: false
---
### 概要
* `UserDefaults`の`bool(forKey:)`について

### 実装しようとしたこと
* `UserDefaults`を使った値でViewの表示制御をすることを考えた際に`UserDefaults`が`nil`であった場合に`false`が入っていないとクラッシュするのでは？と考えた

### 実装したコード
```Swift
.onAppear {
    isEnabledShaking = UserDefaults.standard.bool(forKey: "isShakingEnabled") ?? false
}
```
::: note warn
remove ?? false
:::

* `?? false`以降はどんな条件でも実行されないからremoveしろとアラートで怒られている。はて。

### 仕様の確認
* `bool(forKey:)`を使用する際に値がnilである場合は、自動的に`false`を返してくれるという仕様が存在するとのこと。
* ゆえにこの場合は明示的に`nil`だったら`false`にするなと書かなくてよいらしい。

### 解決
```Swift
.onAppear {
    isEnabledShaking = UserDefaults.standard.bool(forKey: "isShakingEnabled")
}
```
