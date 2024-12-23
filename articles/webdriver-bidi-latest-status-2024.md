---
title: "WebDriver BiDiと最新の実装状況"
emoji: "🤖"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["adventcalendar", "selenium", "puppeteer", "playwright"]
published: true
published_at: 2024-12-24 09:00
---

この記事は[ソフトウェアテストの小ネタ Advent Calendar 2024](https://qiita.com/advent-calendar/2024/software-testing-koneta)の24日目の記事です。
また、12月4日に開催された[Nihonbashi Test Talk #3](https://nihonbashitesttalk.connpass.com/event/334396/)で発表した内容を記事にしたものです。

WebDriver BiDiの概要とブラウザ・自動化ライブラリそれぞれの実装状況をお伝えします。

## WebDriver BiDiとは？

従来のWebDriverとChrome DevTools Protcolの長所を組み合わせたブラウザ自動化の新しい標準プロトコルです。
WebDriver BiDiについては以下のtogamiさんの記事が詳しいです。こちらをご覧ください。

https://zenn.dev/togami2864/articles/65af759b4a34f6

## ブラウザの実装状況

web-platform-testsというテストが用意されており、こちらで確認できます。Chrome系、Firefoxは順調ですが、Safariの実装があまり進んでいないようです。

https://wpt.fyi/results/webdriver/tests/bidi?run_id=5539249372004352&run_id=5161639605436416&run_id=5130708752531456&run_id=5278625924644864

## 自動化ライブラリの実装状況

### Puppeteer

2023年12月6日リリースの[v21.6.0](https://github.com/puppeteer/puppeteer/releases/tag/puppeteer-core-v21.6.0)からWebDriver BiDiでの接続をオプションとしてサポート開始しています。[^1]
その後、今年の8月7日リリースの[v23.0.0](https://github.com/puppeteer/puppeteer/releases/tag/puppeteer-core-v23.0.0)からFirefoxはデフォルトでWebDriver BiDiでの接続になっています（Chromeは引き続きオプション）。
ただし一部のAPIは未実装のようです。

### Playwright

今年の9月頃から開発がスタートしています。現在は内部で実装を試しながらテストをしており、通常利用はできないようです。
以下のissueで課題が管理されており、未解決の課題が列挙されています。
https://github.com/microsoft/playwright/issues/32577

### Selenium

CDPのコマンドを置き換える実装が進んでいます。起動時のオプション設定でWebDriver BiDiを選択することができます。
https://www.selenium.dev/documentation/webdriver/bidi/
同時にWebDriver Classicのコマンドも置き換えるPOCが進んでいます（Java）。
https://github.com/SeleniumHQ/selenium/pull/13190
現在これらはSelenium 5をマイルストーンとして開発が進んでいます。
https://github.com/SeleniumHQ/selenium/milestone/16

## まとめ

- WebDriver BiDiとは新しいブラウザ自動化の標準化プロトコルです
- ブラウザの実装は順調に進んでいます（Safari除く）
- 自動化ライブラリの実装も順調に進んでいます


---

[^1]: 開発自体は2022年9月ごろからスタートしているようです。https://github.com/puppeteer/puppeteer/pull/8932