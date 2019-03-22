# javascript til
## 数値
  - 四捨五入
    `Math.round`  
    `例: Math.round(123.456)    // 123`  
    `例: Math.round(123.567)    // 124`
  - 切り上げ
    `Math.ceil`
    `例： Math.ceil(123.456)    // 124`
    `例： Math.ceil(123.567)    // 124`
  - 切り捨て
    `Math.floor`
    `例： Math.ceil(123.456)    // 123`
    `例： Math.ceil(123.567)    // 123`

## 文字列
  - 全置換  
    × `'a b c'.replace(' ', '-')   // a-b c`  
    ○ `'a b c'.replace(/ /g, '-')  // a-b-c`

## Array
  - 要素を検索  
    `array.indexOf`  
    `console.log(array.indexOf('aaaa'));`
  - 要素を追加  
    `array.push('aaaa')`
  - 要素を削除
    `delete array['aaaa']`
  - サイズ
    `array.length`

