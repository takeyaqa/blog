---
title: "テスト自動化練習サイトのURLを変更します"
emoji: "🌠"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["selenium", "test", "automation", "beginner"]
published: true
---

## まとめ

テスト自動化練習用サイトのURLを以下のように変更します。当該サイトにもすでに記載済みです。

**変更前**
**https://hotel.testplanisphere.dev/**

**変更後**
**https://hotel-example-site.takeyaqa.dev/**

2024年12月1日より新URLでの運用を開始しています。2024年12月中は両方のURLで並行運用をします。
2025年1月1日以降は旧URLへのアクセスは新URLへリダイレクトされる予定です。このリダイレクトは半年から1年程度行われます。

テスト自動化練習用サイトについてはこちらの記事を参照してください（内容がいくらか古くなっていますがご了承ください）。

https://zenn.dev/takeyaqa/articles/automation-testing-practice

https://zenn.dev/takeyaqa/articles/automation-testing-practice-en-us

## 詳しく

### サイトのURL以外に変更となったもの

関連リポジトリのURLも変更になっています。

https://github.com/takeyaqa/hotel-example-site
https://github.com/takeyaqa/hotel-example-selenium4-java-ja
https://github.com/takeyaqa/hotel-example-selenium4-java-en-us

以前は[Test Planisphere](https://github.com/testplanisphere)という組織の所有になっていましたが、現在は私（当該組織の管理者）個人の所有に切り替えています。
また、練習用サイトに簡易なアクセス解析を設置しました。

### 変更の理由について

主に管理上の理由です。前述のTest Planisphereは、この練習用サイトのようなテスト自動化に関する学習リソースやサンプルコードを展開していくつもりでした。
しかし結局のところ、最低限のメンテナンスをするのが精一杯で、最初に作成していたサンプルコードもSelenium4が残るだけとなりました。[^1]
と、細々続けるうちに、もう諸々整理してしまった方がスッキリして良いのでは？　となってお掃除しているのが今です。
GitHub上にあるTest Planisphereにあったリポジトリは全て個人ユーザーの方に移動しました。この組織自体、2025年の半ばくらいにはアーカイブしてしまう予定です[^2]
また、これまで運営者が誰なのか分かりにくかったという問題を解消するために、改めてサイトのフッターなども更新しています。

## さいごに

この4年間でブラウザのテスト自動化をめぐる環境は大きく変わりました。Puppeteer、CypressそしてPlaywrightなどのツールはSelenium一強の勢力を大きく変え、Autify、mabl、MagicPodといったサービスはAI技術を積極的に取り入れて日々進化しています。
この練習用サイトは静的なHTMLとJavaScriptを駆使して、さも動的サイトであるかのように振る舞うよう作られています。採用した技術セットは作成した当時でもかなり枯れていたものです。
現在ではjQueryではなくReactやVueを使うでしょうし、それに伴って全体がSPAに近い構成になるでしょう。デザインもBootstrapではなくTailwindを選択するかもしれません。
自動化の大きな変化として、要素特定の手法がidやCSSセレクターからアクセシビリティ属性へと変わっていったこともあります。ですが、このサイトはアクセシビリティ属性に全く対応していません。

今回のURL変更で管理するものを減らした（または減らす算段がついた）ため、サイト自体は今後も運用を続けていく予定です。とはいえ前述の通り作りが古いかつ、教材という性質上アップグレードもやりづらいものであるため、遠からずお役御免になるのかなと思っています。いつかは生成AIの発展でテスト自動化自体を学ばなくて良くなるかもしれません。

それまでの間となりますが、引き続きご愛顧のほどよろしくお願いいたします🙇

---

[^1]: 当初はWebdriverIOやCapybaraもありました。これらのリポジトリもアーカイブされた状態ですが、個人の所有に移動しています。
[^2]: そもそも所属メンバーが私一人だったので、何が変わるということもないです。
