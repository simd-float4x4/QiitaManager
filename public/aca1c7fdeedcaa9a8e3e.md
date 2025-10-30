---
title: >-
  【SwiftUI】Static method 'buildExpression' requires that 'CustomText' conform to
  'View'
tags:
  - SwiftUI
private: false
updated_at: '2025-10-26T21:05:07+09:00'
id: aca1c7fdeedcaa9a8e3e
organization_url_name: null
slide: false
ignorePublish: false
---
### 発生したエラー
::: note alert
Static method 'buildExpression' requires that 'CustomText' conform to 'View'
:::

### 該当のコード

```Swift
extension String {
    var isAlphanumeric: Bool {
        let range = "[a-zA-Z0-9]+"
        return NSPredicate(format: "SELF MATCHES %@", range).evaluate(with: self)
    }
}

struct CustomText: ViewModifier {
    let contentText: String
 
    func body(content: Content) -> some View {
        let array_text = Array(contentText).map{　String($0)　}
        return HStack(spacing: 0) {
            ForEach(array_text, id: \.self) { item in
                if item.isAlphanumeric == true {
                    Text(item)
                        .font(.custom("Futura", size: 20))
                } else {
                    Text(item)
                        .font(.custom("HiraginoSans-W6", size: 20))
                }
            }
        }
    }
}

// 省略
var body: some View {
    CustomText(contentText: "COVID検査") //エラー発生箇所
}
```

### エラーの発生原因
* `CustomText`が`ViewModifier`型であるため、`View`型に適合していないから。

### 取り組んだこと

#### 1. Viewを拡張して`customText`モディファイアを作る
```diff_swift
+ extension View {
+     func customText(_ text: String) -> some View {
+        self.modifier(CustomText(contentText: text))
+    }
+ }
```

#### 2. `Text`に`Modifier`を適用する

```diff_swift
- Text("COVID検査")
+ Text("")
+    .modifier(CustomText(contentText: "COVID検査"))
```

* 上記対応でエラーが解消した。
