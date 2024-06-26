---
title: "JSTQBとISTQBのシラバスバージョンのまとめ"
emoji: "🪪"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["test", "JSTQB"]
published: true
---

## この記事は？

JSTQBのシラバスはISTQBのシラバス（英語）が公開された後に日本語に翻訳されます。当然ながら翻訳には一定の時間がかかるため、ISTQBのシラバス公開から日本語版のシラバスの公開までにはタイムラグがあります。

筆者は久しぶりにJSTQBのシラバスを読み返そうと考えたのですが、現状のシラバスがはたして最新版なのかを一度確認しておこうと思い、整理を始めました。この記事ではその整理した内容を共有します。

## 各レベル・カテゴリごとのまとめ

ここから現在（2024年5月末）のバージョンをまとめていきます。

JSTQBシラバスのバージョン番号については、原則として翻訳元のISTQBのバージョンに`J01`などの日本語版のバージョンを付加したものになっています。誤訳の修正などが発生した場合にはこの数値のみが上がるしくみです。
また、ISTQBシラバスのバージョン番号についてですが、2020年ごろまでは`v2018`のようにリリース年を使用していたのを、最近では`v4.0`のような数値を使う形式に変えたようです。

### Core Foundation

| 名称 | 略称 | ISTQBバージョン | ISTQBリリース日 | JSTQBバージョン | JSTQBリリース日 |
| --- | --- | --- | --- | --- | --- |
| [Foundation Level](https://www.istqb.org/certifications/certified-tester-foundation-level) | CTFL | v4.0 | 2023-04-21 | v4.0.J01 (v2023V4.0.J01) | 2023-09-25 |

バージョンは最新で揃っているのですが、一点注意があります。**`v4.0`に準拠したCTFLの試験は日本では2024年11月から**となっています。それまでは一つ前のバージョンである`v3.1 (v2018V3.1.J03)`に準拠した試験が実施されています。

### Core Advanced

| 名称 | 略称 | ISTQBバージョン | ISTQBリリース日 | JSTQBバージョン | JSTQBリリース日 |
| --- | --- | --- | --- | --- | --- |
| [Test Management](https://www.istqb.org/certifications/test-manager) | CTAL-TM | v3.0 | 2024-05-03 | v2012.J04 | 2021-02-19 |
| [Test Analyst](https://www.istqb.org/certifications/test-analyst)  | CTAL-TA | v3.1.2 | 2022-01-31 | v3.1.1.J03 | 2021−09−26 |
| [Technical Test Analyst](https://www.istqb.org/certifications/technical-test-analyst) | CTAL-TTA | v4.0 | 2021-06-30 | v2012.J02 | 2018-03-15 |

CTAL-TMは直近で新バージョンがリリースされており、翻訳版はまだ反映されていません。ISTQBのアナウンスによると、非英語圏での旧バージョン（`v2012`）による試験は2025年11月30日までとのことなので、日本でもおおむね1年くらいかけて翻訳と試験の改訂が進むものと思われます。

CTAL-TAは最新版で揃っています（軽微な修正を除く）。

CTAL-TTAは2018年に`v2012`の翻訳が出てから日本語版は更新がありませんが、ISTQBでは`v2019`、`v4.0 (2021)`とバージョンアップされており、日本語版は2バージョン古いものとなってしまっています。現在CTAL-TTAは日本語の試験が無いため、受験したい場合は英語で受験することになりますが、そちらはすでに`v4.0`準拠となっているため注意が必要です。

### Specialist

| 名称 | 略称 | ISTQBバージョン | ISTQBリリース日 | JSTQBバージョン | JSTQBリリース日 |
| --- | --- | --- | --- | --- | --- |
| [AI Testing](https://www.istqb.org/certifications/artificial-inteligence-tester) | CT-AI | v1.0 | 2021-10-01 | v1.0.J01 | 2023-02-25 |
| [Game Testing](https://www.istqb.org/certifications/game-testing) | CT-GaMe | v1.0.1 | 2022-10-21 | - | - |
| [Test Automation Engineer](https://www.istqb.org/certifications/test-automation-engineer) | CT-TAE | v2016 | 2016-10-21 | v2016.J01 | 2020-09-30 |
| [Performance Testing](https://www.istqb.org/certifications/performance-tester) | CT-PT | v2018 | 2018-12-9 | v2018.J01 | 2022-04-16 |
| [Automotive Software Tester](https://www.istqb.org/certifications/automotive-software-tester) | CT-AuT | v2.0.2 (v2018) | 2018-07-04 | v2018.J03 | 2022-08-14 |
| [Usability Testing](https://www.istqb.org/certifications/usability-tester) | CT-UT | v2018 | 2018-07-08 | - | - |
| [Acceptance Testing](https://www.istqb.org/certifications/acceptance-tester) | CT-AcT | v2019 | 2019-06-21 | - | - |
| [Gambling Industry Tester](https://www.istqb.org/certifications/gambling-tester) | CT-GT | v2019 | 2019-03-18 | - | - |
| [Mobile Application Testing](https://www.istqb.org/certifications/mobile-tester) | CT-MAT | v2019 | 2019-05-03 | v2019.J01 | 2021-07-15 |
| [Security Tester](https://www.istqb.org/certifications/security-tester) | CT-SEC | v2016 | 2016-03-18 | - | - |
| [Model-Based Tester](https://www.istqb.org/certifications/model-based-tester) | CT-MBT | v1.1 | 2024-02-23 | - | - |

Specialistは半分ほどが翻訳されており、翻訳されているものはすべて最新版となっています（ISTQB側があまり頻繁に更新していないようです）。

### Agile

| 名称 | 略称 | ISQTBバージョン | ISTQBリリース日 | JSTQBバージョン | JSTQBリリース日 |
| --- | --- | --- | --- | --- | --- |
| [Foundation Level Agile Tester](https://www.istqb.org/certifications/agile-tester) | CTFL-AT | v2014 | 2014-09-30 | v2014.J02 | 2022-07-31 |
| [Advanced Level Agile Technical Tester](https://www.istqb.org/certifications/agile-technical-tester) | CTAL-ATT | v1.1 | 2019-12-09 | v1.1.J01 | 2023-07-09 |
| [Agile Test Leadership at Scale](https://www.istqb.org/certifications/agile-test-leadership-at-scale)  | CT-ATLaS | v2.0 | 2023-09-29 | - | - |

AgileもSpecialistと同様に翻訳されているものはすべて最新版です。

## 最後に

ざっと整理してみました。みなさんの参考になれば幸いです。
