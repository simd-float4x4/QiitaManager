---
title: flutter createしたアプリ名を任意の名称に変更する
tags:
  - Dart
  - Flutter
private: false
updated_at: '2025-10-14T11:37:15+09:00'
id: 84bda7dbcb7cf9bed2c7
organization_url_name: null
slide: false
ignorePublish: false
---
## 環境
・Windows
・Flutter

----

## 手順
・Appという名前でプロジェクトをcreateしてしまったため、任意の名称に変更したい。
・change_app_Package_name（ https://pub.dev/packages/change_app_package_name ）をダウンロードする

```PowerShell
flutter pub add change_app_package_name
```

https://pub.dev/packages/change_app_package_name

またはdependeciesに追記してもよい

```
dev_dependencies: 
  change_app_package_name: ^1.4.0
```

```
> flutter pub add change_app_package_name
Resolving dependencies... 
Downloading packages...
+ change_app_package_name 1.5.0
  characters 1.4.0 (1.4.1 available)
  flutter_lints 5.0.0 (6.0.0 available)
  lints 5.1.1 (6.0.0 available)
  material_color_utilities 0.11.1 (0.13.0 available)
  meta 1.16.0 (1.17.0 available)
  test_api 0.7.6 (0.7.7 available)
Changed 1 dependency!
6 packages have newer versions incompatible with dependency constraints.
```


・`{YOUR_NEW_APP_NAME}`を任意の名称に変更してコマンドを打つ。
```PowerShell
flutter pub run change_app_package_name:main {YOUR_NEW_APP_NAME}
```

* 最後にルートディレクトリの名称を`{YOUR_NEW_APP_NAME}`に変更してリネーム作業終了
