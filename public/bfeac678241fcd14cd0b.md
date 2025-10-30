---
title: 【Swift】AtCoder429 C問題の反省
tags:
  - AtCoder
  - 競技プログラミング
  - Swift
private: false
updated_at: '2025-10-26T21:07:32+09:00'
id: bfeac678241fcd14cd0b
organization_url_name: null
slide: false
ignorePublish: false
---
### 概要
* AtCoder429　C問題についてWAになった問題の見直し

### 該当の問題

https://atcoder.jp/contests/abc429/tasks/abc429_c

### 問題の概要
* ランダムな長さの配列Aの中から3つの要素を取り出して、同じ要素が2個入ってたら`Yes`を出力する

### 方針
* 全組み合わせを検索する必要があり
* `for`ループのネストを使うんだろうな
* A=[0,1,2,3,4] に対して、A=[0]の時に[1...4]を調べてあげるコード書けばいいので、
```Swift
for i in 0 ..< A.count {
 // iをtmpに格納
 for j in i + 1 ..< A.count {
 　// jをtmpに格納
   // tmpに保存したi, jと、j+1の変数を比較, 条件に合致するのであればPASS
 }
}
```

という考えで実装したところWA判定を喰らってしまった。

私が間違えていたのは`i, jと、j+1の変数を比較`の部分で論理演算子`||`を用いて判定したところ。

`tmp[0]`,`tmp[1]`のいずれか一つに合致すればtrueじゃね？と思ったのだが、どうやらそれだとAcceptしてはいけないケースでAcceptしてしまってるらしい。（例：３つ全てが同じ値の時など）

```Swift
if A[j] == tmp_array[0] || A[j] == tmp_array[1] 
```

### 解決策の検討

```Swift
for i in 0..<N {
    for j in i+1..<N {
        for k in j+1..<N {
            let set = Set([A[i], A[j], A[k]])
            if set.count == 2 {
                answer += 1
            }
        }
    }
}
```

* メモリのタイムアウトになりそうだが、forループを3つ使ってもよかったかもしれない。
* `Set`関数を用いることで重複する値を排除することができる。
* 故に2種類の値が配列の中にあれば、条件`true`を満たせそうである
