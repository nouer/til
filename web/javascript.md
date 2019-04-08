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

## async/await
  - Promiseオブジェクトを返す
<pre>
return new Promise((resolve, reject) => {

});
</pre>
  - Promiseの結果を返す(resolve)
<pre>
return new Promise((resolve, reject) => {
    resolve('result = resolve');
});
</pre>
  - Promiseの結果を返す(reject)
<pre>
return new Promise((resolve, reject) => {
    reject('result = reject');
});
</pre>
  - 非同期関数の定義
<pre>
async function sample() {}
</pre>
  - サンプル1
<pre>
// resolve1!!をreturnしているため、この値がresolveされる
async function resolveSample() {
    return 'resolve!!';
}

// resolveSampleがPromiseを返し、resolve!!がresolveされるため
// then()が実行されコンソールにresolve!!が表示される
resolveSample().then(value => {
    console.log(value); // => resolve!!
});


// reject!!をthrowしているため、この値がrejectされる
async function rejectSample() {
    throw new Error('reject!!');
}

// resolveSampleがPromiseを返し、reject!!がrejectされるため
// catch()が実行されコンソールにreject!!が表示される
rejectSample().catch(err => {
    console.log(err); // => reject!!
});


// resolveErrorはasync functionではないため、Promiseを返さない
function resolveError() {
    return 'resolveError!!';
}

// resolveErrorはPromiseを返さないため、エラーが発生して動かない
// Uncaught TypeError: resolveError(...).then is not a function
resolveError().then(value => {
    console.log(value);
});
</pre>
  - サンプル2
<pre>
function sampleResolve(value) {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve(value * 2);
        }, 2000);
    })
}

/**
 * sampleResolve()をawaitしているため、Promiseの結果が返されるまで処理が一時停止される
 * 今回の場合、2秒後にresolve(10)が返ってきてその後の処理（return result + 5;）が再開される
 * resultにはresolveされた10が格納されているため、result + 5 = 15がreturnされる
 */
async function sample() {
    const result = await sampleResolve(5);
    return result + 5;
}

sample().then(result => {
    console.log(result); // => 15
});
</pre>

## console.log
  - object  
    `%o, %O`
  - integer  
    `%d, %i`
  - string  
    `%s`
  - floting-point number  
    `%f`
  - css  
    `%c`
## console.group
  console.groupで開始して、console.gourpEndで終了する  

    console.group();
    console.log("Inside 1st group");
    console.group();
    console.log("Inside 2nd group");
    console.groupEnd();
    console.groupEnd();
    console.log("Outer scope");

## console.trace
  スタックトレースの出力ができる

## console.time
  - console.ltime
  - console.timeLog
  - console.timeEnd

## console.count
  console.countでカウント表示  
  console.countResetでリセット

    console.count();
    console.count('1stcount')  
    console.count('2ndcount');
    console.lcuntReset();
    console.lcuntReset('1stcount');
    console.lcuntReset('2ndcount');

## console.table
  テーブルで配列を表示  

    console.table([[0,1,2,3,4], [5,6,7,8,9]]);

