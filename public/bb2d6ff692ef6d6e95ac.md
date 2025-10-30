---
title: 【Flutter】TextFieldのPlaceholderに文字色をセットしたい
tags:
  - Dart
  - Flutter
private: false
updated_at: '2025-10-16T14:08:14+09:00'
id: bb2d6ff692ef6d6e95ac
organization_url_name: null
slide: false
ignorePublish: false
---
### やりたいこと
* `TextField`の`hintText`のプレースホルダに色を設定したい。

```edit_title_view.dart
TextFormField(
    controller: _titleController,
    hintText: "put something here",
    onFieldSubmitted: (value){},
)
```

### 解決策
* `InputDecoration`の`hintStyle`は`TextStyle`の型を継承しているため通常の`Text`と同様に加工をすることが出来る。

```edit_title_view.dart
TextFormField(
    controller: _titleController,
    hintText: "put something here",
    hintStyle: TextStyle(
        color: Colors.grey,
        fontSize: 10
    ),
    onFieldSubmitted: (value){},
)
```
