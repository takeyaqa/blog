---
title: "Chrome 111でSelenium(Java)がエラーになる現象の対処"
emoji: "🙆"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["selenium", "test", "automation", "chrome"]
published: true
---

https://twitter.com/titusfortner/status/1633524991848243207

Titusさん（Seleniumプロジェクトメンバー）のツイートの通りなのですが、Chrome 111 でSelenium(Java)を使おうとした場合、WebDriverの起動時にエラーが発生するようになっています。
日本語で言及している方があんまりいなさそうだったので、この記事ではこのエラーの対処方法について解説します。

## 原因

https://github.com/SeleniumHQ/selenium/issues/11750

このエラーはJava向けのSeleniumでのみ発生します。
SeleniumではChromeのDevtoolsと通信を行っています。Chrome 111でこの通信の仕様が少し変更になったのですが、Seleniumが使っているHTTP Clientがこれに対応できないためエラーとなります。HTTP ClientはJava 8への対応維持から古いライブラリが使われており、このライブラリは現在メンテナンスがされていないそうです。

## Java 11, 17以上の場合

前述の問題からSeleniumのHTTP Clientをアップデートするプロジェクトが動いています。Java 11からは標準ライブラリでWebSocketまで対応可能なのでそちらを使うようです。これは以下の手順で有効化でき、有効化によって前述のエラーは回避できます。

https://www.selenium.dev/blog/2022/using-java11-httpclient/#integrating-the-java-11-client


### 依存ライブラリの追加

Mavenの場合

```xml
<dependency>
  <groupId>org.seleniumhq.selenium</groupId>
  <artifactId>selenium-java</artifactId>
  <version>4.8.1</version>
</dependency>
<dependency>
  <groupId>org.seleniumhq.selenium</groupId>
  <artifactId>selenium-http-jdk-client</artifactId>
  <version>4.8.1</version>
</dependency>
```

Gradleの場合

```gradle
dependencies {
    testImplementation 'org.seleniumhq.selenium:selenium-java:4.8.1'
    testImplementation 'org.seleniumhq.selenium:selenium-http-jdk-client:4.8.1'
}
```

### コードの変更

`WebDriver` の初期化前に `System.setProperty("webdriver.http.factory", "jdk-http-client");` を追加します。

```java
System.setProperty("webdriver.http.factory", "jdk-http-client");
WebDriver driver = new ChromeDriver();
```

この状態で起動すると新しいHTTP Clientが使用され、エラーを回避できます。

## Java 8の場合

Java 8の場合HTTP Clientの変更ができないため、Chromeの設定を変更します。以下の引数を指定することでエラーが回避できます。
ただしこの設定はわずかにセキュリティリスクが発生するため[^1]、可能ならJava 11以上にアップデートすることを推奨しています。

```java
ChromeOptions options = new ChromeOptions();
options.addArguments("--remote-allow-origins=*");
WebDriver driver = new ChromeDriver(options);
```

## まとめ

Chrome 111でのエラーを回避する方法を紹介しました。Seleniumプロジェクトでは近い将来にJava 8のサポートを終了することを検討しているそうです。これを機にJava 11以上にアップデートするのも良いでしょう。

---

[^1]: 実際に問題になることはほぼないです