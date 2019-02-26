# HTML知識

## css, javascriptの読み込み順  
  - BODYの最後に書く  
    - javascriptを読み込んでいる間はhtmlの読み込みが中断されるので、レンダリングを早くしたい場合、非同期で読み込ませるasyncという属性もある  
  - HEADに書く
    - レンダリングされる前にjavascriptを読み込みたい場合

## FlexBox
  - [チートシート](https://www.webcreatorbox.com/tech/css-flexbox-cheat-sheet)

## iOS + Safari
  - Invalid Dateに気をつける  
    iOSのSafariでJavaScriptで日付フォーマットを渡すとき、2019-02-22 などのように '-' でセパレートした文字列を渡すと、Invalid Dateになる。  
    chart.js で iOS + Safari でグラフが表示されない等は、この日付フォーマットの問題に起因することがよくある。
