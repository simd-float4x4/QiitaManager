---
title: 【XCode26】ファイルの新規作成にマイナーアップデート（New Files From Template）
tags:
  - Swift
  - iOS26
  - Xcode26
private: false
updated_at: '2025-10-17T17:39:36+09:00'
id: 83cc23fe3ac2dc5cb2fc
organization_url_name: null
slide: false
ignorePublish: false
---
* XCode26に個人的にはあまり好きではない改変があったので共有


### 変更点
* ディレクトリ上でファイルの新規作成を行うときに表示されるメニューが[New Empty File]と[New File From Template]の2つに枝分かれしました。

![スクリーンショット 2025-10-17 13.49.20.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/4049147/a0371664-9f08-49a1-9a5c-b3d77397a614.png)


* 従来のテンプレートを表示する際は[New File From Template]を、空ファイルを作りたい時は[New Empty File]をクリックする必要があります。

![スクリーンショット 2025-10-17 13.49.26.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/4049147/0abc5548-4dce-49e0-9283-99bb0e6c204b.png)

* テンプレートから作りたいのに間違えて[New Empty File]をクリックしてしまうと、二度手間になってしまうよというお話でした。
