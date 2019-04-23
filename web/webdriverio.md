# WebDriverIO
  [WebDriverIO 公式](https://webdriver.io/)

## WebDriverIOとは
  - Node.js上で、Selenium WebDriverを操作できるnpm package

## Mode
  - Standalone  
    スクレイピング用
  - WDIO  
    E2Eテスト用

## Standalone Mode
  - サンプル  

    ```js  
    const webdriverio = require('webdriverio');
    const options = { desiredCapabilities: { browserName: 'chrome' } };
    const client = webdriverio.remote(options);
    
    client
        .init()
        .url('https://duckduckgo.com/')
        .setValue('#search_form_input_homepage', 'WebdriverIO')
        .click('#search_button_homepage')
        .getTitle().then(function(title) {
            console.log('Title is: ' + title);
            // outputs: "Title is: WebdriverIO (Software) at DuckDuckGo"
        })
        .end();
    ```  

## WDIO Mode
  - サンプル

    ```js  
    const assert = require('assert');
    
    describe('Google', function() {
      it('should display the title', function() {
          browser.url('https://www.google.co.jp/');
          assert(browser.getTitle() === 'Google');
      });  
    });
    ```  

  - WDIO Modeでは、テストランナーを使って記述を行う

## Selenium 環境作作成
  1. [Selenium Standalone Server](https://www.seleniumhq.org/download/) を導入   

      ```shell
      $ npm install selenium-standalone@latest -g
      $ selenium-standalone install
      ```
  1. Selenium Standalone Server を起動

      ```shell
      $ selenium-standalone start
      ```
  
  1. WebdriverIO REPL Interface の起動方法

      ```shell
      $ ./node_modules/.bin/wdio repl chrome
      ```

  1. スクリプトを作成  

      ```js
      'use strict';
    
      var webdriverio = require('webdriverio');
    
      var client = webdriverio
      .remote({ desiredCapabilities: { browserName: 'chrome' } })
      .init()
      .url('https://www.google.com/');
    
      client
      .getTitle()
      .then(function (title) {
        console.log(title);
      })
      .getHTML('body')
      .then(function (data) {
        console.log(data);
      })
      .end();
      ``` 

  1. webio.conf.js の作成
      ```js
      ```

  1. スクリプトの実行
      ```shell
      ./node_modules/.bin/wdio webio.conf.js
      ```

---
---

↓　削除分


# WebdriverIO
## Selenium 環境作作成
  1. [Selenium Standalone Server](https://www.seleniumhq.org/download/) を導入   

      ```shell
      npm install --save-dev selenium-standalone

      npm install --save webdriverio
      npm install --save @wdio/cli
      
      
      # テストフレームワークのインストール
      npm install --save-dev wdio-mocha-framework
      npm install --save-dev chai
      
      # レポーター(テスト結果の表示ツール)の導入。お好みで
      npm install --save-dev wdio-dot-reporter
      npm install --save-dev wdio-junit-reporter
      npm install --save-dev wdio-spec-reporter
      ```

  1. configの作成
      ```shell
      $ ./node_modules/.bin/wdio config
      ```
      表示される質問に答える、YESでよい  
      作成された`wdio.conf.js`の`cabpabilities`の`browserName`を`chrome`に変更する

  1. テストスクリプトを作成する
      ```js
      var assert = require('assert');
      describe('webdriver.io page', function() {
          it('should have the right title - the fancy generator way', function () {
              browser.url('http://webdriver.io');
              var title = browser.getTitle();
              assert.equal(title, 'WebdriverIO - WebDriver bindings for Node.js');
          });
      });
      ```

  1. WebdriverIOを実行

      ```shell
      $ ./node_modules/.bin/wdio
      ```
