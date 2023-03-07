---
title: "Github Actions+AppiumでiPhone Simulatorを動かす"
emoji: "📱"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["test", "appium", "githubactions", "ios", "ci"]
published: true
published_at: 2019-09-25 09:00
---

Github Actionsの環境にAppiumをインストールをしてiPhone Simulator上のSafariでブラウザの自動テストを実行する方法を共有します。

<!--more-->

[Github Actions仮想環境のインストール済みソフトウェア](https://help.github.com/en/articles/software-in-virtual-environments-for-github-actions)見てたらiPhone Simulatorインストール済みだったので普通にいけるのでは？と思いやってみたらできました。内容としてはAppiumをインストールしてSimulatorの制御とかはそちらに任せる感じです。


## 参考記事

https://qiita.com/mizchi/items/9c03df347748ba5f5a11

## ワークフロー定義

```yaml
name: iPhone Simulator Test

on: [push, pull_request]

jobs:
  build:
    name: Safari Test
    runs-on: macOS-10.14
    steps:
      - name: Checkout source code
        uses: actions/checkout@v1
      - name: Set up Node.js
        uses: actions/setup-node@v1
        with:
          node-version: '10.16.3'
      - name: Set up Appium
        run: npm install appium
      - name: Run Appium Server
        run: ./node_modules/.bin/appium --log-timestamp --log-no-colors > appium.log &
      - name: Build with Gradle
        run: gradle cleanTest test --tests "com.example.safari.MobileSafariTest"
        continue-on-error: true
      - name: Upload logs
        uses: actions/upload-artifact@v1
        with:
          name: appium.log
          path: appium.log
      - name: Upload screenshots
        uses: actions/upload-artifact@v1
        with:
          name: screenshots
          path: screenshots

```

1. Nodeをセットアップした後にnpmでAppiumをインストールします
2. `./node_modules/.bin/appium > appium.log &` でログをあとで見れるように、またバックグラウンドプロセスになるようにしてAppiumサーバーを起動します、またログへのタイムスタンプ付加などのオプションを追加しています
3. JavaをセットアップしてGradleでテストを実行します
4. `actions/upload-artifact` でスクリーンショットとログを保存します。保存したログ等はActionsの画面からダウンロードが可能です。

![artifactsのダウンロード画面](/images/2019/09/25/01_artifacts.png)

## テストコード

コードはJava+JUnit5です。Qiitaにアクセスして文字入力して検索するだけですね。

```java
  @BeforeEach
  void before() {
    DesiredCapabilities caps = new DesiredCapabilities();
    caps.setBrowserName(BrowserType.SAFARI);
    caps.setCapability(MobileCapabilityType.AUTOMATION_NAME, AutomationName.IOS_XCUI_TEST);
    caps.setCapability(MobileCapabilityType.DEVICE_NAME, "iPhone X");
    caps.setCapability(MobileCapabilityType.PLATFORM_VERSION, "12.4");
    caps.setCapability(MobileCapabilityType.LANGUAGE, "ja");
    caps.setCapability(MobileCapabilityType.LOCALE, "ja_JP");
    try {
      driver = new IOSDriver<>(new URL("http://0.0.0.0:4723/wd/hub"), caps);
    } catch (MalformedURLException ign) {
      // ignore
    }
  }

  @AfterEach
  void after() {
    if (driver != null) {
      driver.quit();
    }
  }

  @Test
  void testGet() {
    driver.get("https://qiita.com/");

    assertEquals("Qiita", driver.getTitle());
    screenshot();

    driver.get("https://qiita.com/search");
    driver.findElement(By.id("q")).sendKeys("Selenium");
    screenshot();
    driver.findElement(By.className("searchResultContainer_searchButton")).click();
    (new WebDriverWait(driver, 10)).until(ExpectedConditions.titleContains("Selenium"));
    assertEquals("「Selenium」の検索結果 - Qiita", driver.getTitle());
    screenshot();
  }
```

## まとめと課題

あんまり効率が良さそうには見えないのでキャッシュとかうまく効くようにしたいですね。WebDriverIOとか使ってJavaScriptでコード書けば全体はスッキリすると思います。

シミュレーターの定義は`deviceName`と`platformVersion`の組み合わせで決まるので、ここを環境変数から取得するようにすればマトリックスビルドにも対応できそう。

こんな感じです。AndroidもSDK入ってるしエミュレーター動かせそうな気はします（重そうだけど）。
