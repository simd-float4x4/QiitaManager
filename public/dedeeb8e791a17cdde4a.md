---
title: 【SwiftUI】.cornerRadiusが効かない
tags:
  - SwiftUI
private: false
updated_at: '2025-10-20T14:54:25+09:00'
id: dedeeb8e791a17cdde4a
organization_url_name: null
slide: false
ignorePublish: false
---
### 実現しようとしたこと
* 共通コンポーネントのButtonに角丸を適用する

### 該当コード

```Component.swift
struct ButtonComponents: View {
    @State var buttonText: String
    var body: some View {
        Button(action: {
            print("tap buton")
        }) {
            Text(buttonText)
                .bold()
        }
        .frame(maxWidth: .infinity)
        .frame(maxHeight: 48)
        .cornerRadius(16)
        .accentColor(.white)
        .background(Color.getRawColor(hex: "0017C1"))
    }
}
```

### 不具合の原因
* まず角丸を設定していた順番が良く無い。角丸の後にfillしてしまっているから効いていない。fillしてから角丸を設定する。


* あとiOS26.1でcornerRadiusが`deprecated`になってるで注意（いつから？2023年には既に非推奨になっていたらしい）。

https://developer.apple.com/documentation/swiftui/view/cornerradius(_:antialiased:)

### clipShapeを使いましょうということ

* 以前からこの方法はありましたが、`.cornerRadius`ではなく`RoundedRectancle`を用いて`.clipShape`する方法をとりましょう。

### 直した

```Component.swift
struct ButtonComponents: View {
    @State var buttonText: String
    var body: some View {
        Button(action: {
            print("tap buton")
        }) {
            Text(buttonText)
                .bold()
        }
        .frame(maxWidth: .infinity)
        .frame(maxHeight: 48)
        .accentColor(.white)
        .background(Color.getRawColor(hex: "0017C1"))
        .clipShape(RoundedRectangle(cornerRadius: 8))
    }
}
```
