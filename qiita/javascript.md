# 進捗
- 2016/10/04 記述開始
- 2016/10/05 作成中

---

# 実行環境
[JSFiddle](http://jsfiddle.net/) にアクセス

ブラウザ上の開発者ツールを利用

- Google Chrome

```
[Google Chromeの設定] → [その他のツール] → [デベロッパーツール]
```

- Safari

```
[開発] → [Webインスペクタの表示]
```

- Microsoft Edge

```
[詳細] → [開発者ツール]
```

- Firefox

```
[開発者ツール] → [開発ツールを表示]
```

---

# Hello world
```
console.log("Hello world");
```

---

# コメント
- 単行

```
// コメント
```

- ブロック

```
/* コメント*/
```

---

# 変数/定数
```
"use strict"

var hoge = "hoge";
console.log("Hello world. " + hoge);

let huga = "huga";
console.log("Hello world(ES2015). " + huga);

const const_hoge = "const_hoge";
console.log("Hello world. " + const_hoge);

let number_hoge = 0xFFFFFFFFFFFFFFFF;
console.log("number_hoge = " + number_hoge);

let string_hoge = "0xFFFFFFFFFFFFFFFF";
console.log("string_hoge = " + string_hoge);

let boolean_hoge = true;
console.log("boolean_hoge = " + boolean_hoge);

let array_hoge = [10, 20, 30];
console.log("array_hoge[2] = " + array_hoge[2]);
```

```
Console出力

Hello world. hoge
Hello world(ES2015). huga
Hello world. const_hoge
number_hoge = 18446744073709552000
string_hoge = 0xFFFFFFFFFFFFFFFF
boolean_hoge = true
array_hoge[2] = 30
```

---

# 代入演算子

```
// =
// +=
// -=
// *=
// /=
// %=
// &=
// |=
// ^=
// <<=
// >>=
// >>>=
```

# ビット演算子
- ビット論理演算子

```
```

- ビットシフト演算子

```
```

# delete演算子

```
"use strict"

let hoge = {x: 1, y:2};
console.log(hoge.x);
console.log(delete hoge.x);
console.log(hoge.x);

let fuga = ["x", "y", "z"];
console.log(fuga[0]);
console.log(fuga[1]);
console.log(fuga[2]);
console.log(delete fuga[1]);
console.log(fuga[0]);
console.log(fuga[1]);
console.log(fuga[2]);
```

```
Console出力

1
true
undefined
x
y
z
x
undefined
z
```

# instanceof演算子
# typeof演算子

```
"use strict"

let number_hoge = 1;
console.log(typeof number_hoge);

let string_hoge = "aaaa";
console.log(typeof string_hoge);

let boolean_hoge = true;
console.log(typeof boolean_hoge);

let array_hoge = [0, 1, 2];
console.log(typeof array_hoge);

let map_hoge = {x: "aaa", y: "bbb"};
console.log(typeof map_hoge);
```

```
Console出力

number
string
boolean
object
object
```

# void演算子

---

# 文字列操作
- 文字列定義 / テンプレート文字列

```
"use strict"

let hoge = "hoge";
let fuge = `my name is ${hoge}`;
console.log(hoge);
console.log(fuge);
```

```
Console出力
hoge
my name is hoge
```

- 長さの取得

```
"use strict"

let hoge = "hoge";
console.log(hoge.length);
```

```
Console出力

4
```

- 空設定 / 空判定

```
"use strict"

let hoge = "hoge";
console.log("hoge = " + hoge + ".");

hoge = "";
console.log("hoge = " + hoge + ".");

if (hoge == "") {
	console.log("hoge is empty");
}
```

```
Console出力

hoge = hoge.
hoge = .
hoge is empty
```

- 部分取得
  - charAt
  - slice
  - substring
  - substr
  - split

- 大文字・小文字変換
  - toLowerCase
  - toUpperCase
  
- 文字コード変換
  - charCodeAt
  - fromCharCode
  - codePointAt
  - fromCodePoint

- 連結
  - concat
  
- 空白除去
  - trim

- 置換
  - replace

- 検索
  - indexOf
  - lastIndexOf
  - startsWith
  - endsWith
  - includes

- 正規表現
  - match
  - replace
  - search

- 繰り返し文字の取得
  - repeat

- サロゲートペア

```
"use strict"

let hoge = '𩸽だ';

console.log(hoge.length);

function stringToArray (str) {
    return str.match(/[\uD800-\uDBFF][\uDC00-\uDFFF]|[^\uD800-\uDFFF]/g) || [];
}

console.log(stringToArray(hoge).length);
```

```
Console出力

3
2
```

---

# 数値操作
- 2進数 / 10進数 / 16進数

```
"use strict"

let number_10 = 100;
let number_16 = 0x64;
let number_8 = 0o144;
let number_2 = 0b1100100;
let number_float = 3.14;

console.log("number_10 = " + number_10);
console.log("number_16 = " + number_16);
console.log("number_8 = " + number_8);
console.log("number_2 = " + number_2);
console.log("number_float = " + number_float);
```

```
Console出力

number_10 = 100
number_16 = 100
number_8 = 100
number_2 = 100
number_float = 3.14
```

- Numberのプロパティ
 - MAX_VALUE …　最大の値 1.79E + 308
 - MAX_SAFE_INTEGER …　最大の整数
 - MIN_VALUE …　最小の値
 - NaN …　数値ではない値
 - NEGATIVE_INFINITY …　負の無限大
 - POSITIVE_INFINITY …　正の無限大

```
"use strict"

console.log(Number.MAX_VALUE);
console.log(Number.MAX_SAFE_INTEGER);
console.log(Number.MIN_VALUE);
console.log(Number.NaN);
console.log(Number.NEGATIVE_INFINITY);
console.log(Number.POSITIVE_INFINITY);
```

```
Console出力

1.7976931348623157e+308
9007199254740991
5e-324
NaN
-Infinity
Infinity
```

- 算術演算

```
"use strict"

// +
let hoge = 1 + 9;

// -
let fuga = 11 - 1;

// *
let mogu = 2 * 5;

// /
let gyafu = 20 / 2;

// %
let peke = 110 % 100;

// ++
let maru_src1 = 10;
let maru1 = maru_src1++;

let maru_src2 = 9;
let maru2 = ++maru_src2;

// --
let batu_src1 = 10;
let batu1 = batu_src1++;

let batu_src2 = 11;
let batu2 = --batu_src2;

console.log(hoge);
console.log(fuga);
console.log(mogu);
console.log(gyafu);
console.log(peke);
console.log(maru1);
console.log(maru2);
console.log(batu1);
console.log(batu2);

// shift
let shift_left = 2;
let shift_right = 64;

console.log(shift_left <<= 2);
console.log(shift_right >>= 3);
```

```
Console出力

10
10
10
10
10
10
10
10
10
8
8
```

- 誤差

```
"use strict"

let hoge = 0.1 * 3;
console.log(hoge);
console.log(hoge === 0.3);

let fuga = 0.1 * 10 * 3 / 10;
console.log(fuga);
console.log(fuga === 0.3);
```

```
Console出力

0.30000000000000004
false
0.3
true
```

- 四捨五入 / 小数点切捨て / 切上げ

```
"use strict"

console.log(Math.ceil(1234.56));    // 切上げ
console.log(Math.ceil(-1234.56));   // 切上げ
console.log(Math.floor(1234.56));   // 切り捨て
console.log(Math.floor(-1234.56));  // 切り捨て
console.log(Math.trunc(1234.56));   // 切り捨て
console.log(Math.trunc(-1234.56));  // 切り捨て
console.log(Math.round(1234.56));   // 四捨五入
console.log(Math.round(-1234.56));  // 四捨五入
```

```
Console出力

1235
-1234
1234
-1235
1234
-1234
1235
-1235
```

- 桁あわせ

```
"use strict"

let hoge = 123.4567;
console.log(hoge.toFixed(3));  // 桁あわせ（小数部）
console.log(hoge.toFixed(10)); // 桁あわせ（小数部）
console.log(hoge.toFixed(0));  // 桁あわせ（小数部）
console.log(hoge.toPrecision(3));  // 桁あわせ（全体）
console.log(hoge.toPrecision(10)); // 桁あわせ（全体）
```

```
Console出力

123.457
123.4567000000
123
123
123.4567000
```

- Math
  - ランダム　…　Math.random
  - 絶対値　…　Math.abs
  - 最大値　…　Math.max
  - 最小値　…　Math.min
  - べき乗　…　Math.pow
  
```
"use strict"

console.log(Math.abs(10));
console.log(Math.abs(-10));
console.log(Math.max(-1, 0, 10, 100));
console.log(Math.min(-1, 0, 10, 100));
console.log(Math.pow(2, 8));
console.log(Math.floor(Math.random() * 10)); // 0から9
```

```
Console出力

10
10
100
-1
256
8
```

---

# 時間操作
- 時間の加減（年 / 月 / 日 / 時 / 分 / 秒）
  - （月と年の加減は存在しない日付に気をつける）

```
"use strict"

let src1 = new Date("2016/01/01");
// 年が-1する場合
let dest1 = new Date(new Date(src1).setMonth(src1.getMonth() - 1));
console.log(dest1);
// 年が+1する場合
let dest2 = new Date(new Date(src1).setMonth(src1.getMonth() + 12));
console.log(dest2);
// 月が+1する場合
let dest3 = new Date(new Date(src1).setDate(src1.getDate() + 31));
console.log(dest3);
// 月が-1する場合
let dest4 = new Date(new Date(src1).setDate(src1.getDate() - 1));
console.log(dest4);

// setMonthの罠
let src2 = new Date("2016/08/31");
console.log(src2);
let dest5 = new Date(src2);
dest5.setMonth(4-1);
dest5.setDate(1);
console.log(dest5);  // 期待するのは4/1だが、5/1になる
let dest6 = new Date(src2);
dest6.setDate(1);
dest6.setMonth(4 - 1);
console.log(dest6);  // 4/1 日付から設定すれば問題ない
```

```
Console出力

Tue Dec 01 2015 00:00:00 GMT+0900 (東京 (標準時))
Sun Jan 01 2017 00:00:00 GMT+0900 (東京 (標準時))
Mon Feb 01 2016 00:00:00 GMT+0900 (東京 (標準時))
Thu Dec 31 2015 00:00:00 GMT+0900 (東京 (標準時))
Wed Aug 31 2016 00:00:00 GMT+0900 (東京 (標準時))
Sun May 01 2016 00:00:00 GMT+0900 (東京 (標準時))
Fri Apr 01 2016 00:00:00 GMT+0900 (東京 (標準時))
```

- UTC/Local

```
let today = new Date();
console.log(today.toString());
console.log(today.toDateString());
console.log(today.toTimeString());
console.log(today.toLocaleString());
console.log(today.toLocaleDateString());
console.log(today.toLocaleTimeString());
console.log(today.toISOString());
```

```
Console出力

Wed Oct 05 2016 08:40:43 GMT+0900 (東京 (標準時))
Wed Oct 05 2016
08:40:43 GMT+0900 (東京 (標準時))
2016/10/5 8:40:43
2016/10/5
8:40:43
2016-10-04T23:40:43.122Z
```

---

# null/undefined

```
"use strict"

let hoge;
let fuga = {x: "1"};
console.log("hoge = " + hoge);
console.log("fuga.y = " + fuga.y);

let null_hoge = null;
console.log("null_hoge = " + null_hoge);
```

```
Console出力

hoge = undefined
fuga.y = undefined
null_hoge = null
```

---

- 判定
  - Number.isNaN
  - Number.isFinite
  - Number.isInteger
  - Number.isSafeInteger

---

# 乱数
- Math.random

```
"use strict"

console.log(Math.floor(Math.random() * 10)); // 0 から 9
console.log(Math.floor(Math.random() * 5) + 5); // 5 から 9

let hoge = ["a", "b", "c"];
console.log(hoge[Math.floor(Math.random() * hoge.length)]); // 配列からランダム
```

```
Console出力

2
9
c
```

---

# 型変換

- 数値　→　文字列

```
"use strict"

let hoge = 64;
let fuga10 = hoge.toString(10);
let fuga16 = hoge.toString(16);
let fuga8 = hoge.toString(8);
let fuga2 = hoge.toString(2);
console.log(fuga10);
console.log(fuga16);
console.log(fuga8);
console.log(fuga2);

// カンマ付加
let hoge_commma = 123456789;
console.log(hoge_commma.toLocaleString());

// カンマ付加（正規表現）
function addcomma(num){
    return String(num).replace( /(\d)(?=(\d\d\d)+(?!\d))/g, '$1,');
}
console.log(addcomma(hoge_commma));

// ゼロ付加（zero padding）
// （整数部の長さでzero padding)
function zeroPadding(number, length){
return number.toLocaleString("ja-JP" ,{useGrouping:false , minimumIntegerDigits:length});
}
let hoge1 = 1;
console.log(zeroPadding(hoge1, 20));
let hoge1_1 = 1.1;
console.log(zeroPadding(hoge1_1, 20));

// ゼロ付加（zero padding)
// （全体の長さでzero padding)
function zeroPaddingByArray(number, length){
    return (Array(length).join('0') + number).slice(-length);
}
let hoge2 = 2;
console.log(zeroPaddingByArray(hoge2, 20));
let hoge2_2 = 2.2;
console.log(zeroPaddingByArray(hoge2_2, 20));
``` 

```
64
40
100
1000000
123,456,789
123,456,789
00000000000000000001
00000000000000000001.1
00000000000000000002
000000000000000002.2
```

- 文字列　→　数値

```
"use strict"

let hoge10 = "64";
let fuga10 = Number.parseInt(hoge10);
console.log(fuga10);

let hoge16 = "0xFF";
let fuga16 = Number.parseInt(hoge16, 16);
console.log(fuga16);

let hoge_float = "3.14";
let fuga_float = Number.parseFloat(hoge_float);
console.log(fuga_float);
```

```
Console出力

64
255
3.14
```

- 文字列　⇔　日付

```
"use strict"

console.log(new Date("2016/10/05"));
console.log(new Date("2016-10-05"));
console.log(new Date("2016/10/05 08:03:00"));
console.log(new Date("2016-10-05 08:04:00"));
console.log(new Date("2016-10-05T08:05:00Z"));	// 17:05 in Tokyo(+9)
console.log("----");
let today = new Date();
console.log(today.toString());
console.log(today.toDateString());
console.log(today.toTimeString());
console.log(today.toLocaleString());
console.log(today.toLocaleDateString());
console.log(today.toLocaleTimeString());
console.log(today.toISOString());
```

```
Console出力

Wed Oct 05 2016 00:00:00 GMT+0900 (東京 (標準時))
Wed Oct 05 2016 09:00:00 GMT+0900 (東京 (標準時))
Wed Oct 05 2016 08:03:00 GMT+0900 (東京 (標準時))
Wed Oct 05 2016 08:04:00 GMT+0900 (東京 (標準時))
Wed Oct 05 2016 17:05:00 GMT+0900 (東京 (標準時))
----
Wed Oct 05 2016 08:40:43 GMT+0900 (東京 (標準時))
Wed Oct 05 2016
08:40:43 GMT+0900 (東京 (標準時))
2016/10/5 8:40:43
2016/10/5
8:40:43
2016-10-04T23:40:43.122Z
```

> 日付フォーマットについては JavaScript Date Formatを利用すると便利（[Java Script Date Format](http://blog.stevenlevithan.com/archives/date-time-format)）

>```blog.stevenlevithan.com/archives/date-time-format
> var now = new Date();
> 
> now.format("m/dd/yy");
> // Returns, e.g., 6/09/07
> 
> // Can also be used as a standalone function
> dateFormat(now, "dddd, mmmm dS, yyyy, h:MM:ss TT");
> // Saturday, June 9th, 2007, 5:46:21 PM
> 
> // You can use one of several named masks
> now.format("isoDateTime");
> // 2007-06-09T17:46:21
> 
> // ...Or add your own
> dateFormat.masks.hammerTime = 'HH:MM! "Can\'t touch this!"';
> now.format("hammerTime");
> // 17:46! Can't touch this!
> 
> // When using the standalone dateFormat function,
> // you can also provide the date as a string
> dateFormat("Jun 9 2007", "fullDate");
> // Saturday, June 9, 2007
> 
> // Note that if you don't include the mask argument,
> // dateFormat.masks.default is used
> now.format();
> // Sat Jun 09 2007 17:46:21
> 
> // And if you don't include the date argument,
> // the current date and time is used
> dateFormat();
> // Sat Jun 09 2007 17:46:22
> 
> // You can also skip the date argument (as long as your mask doesn't
> // contain any numbers), in which case the current date/time is used
> dateFormat("longTime");
> // 5:46:22 PM EST
> 
> // And finally, you can convert local time to UTC time. Either pass in
> // true as an additional argument (no argument skipping allowed in this case):
> dateFormat(now, "longTime", true);
> now.format("longTime", true);
> // Both lines return, e.g., 10:46:21 PM UTC
> 
> // ...Or add the prefix "UTC:" to your mask.
> now.format("UTC:h:MM:ss TT Z");
> // 10:46:21 PM UTC
> ```

曜日を日本語で取得する場合

```
"use strict"

var hoge = '日月火水木金土'[new Date("2016/10/05").getDay()];
console.log(hoge);
```

```
Console出力

水
```

元号を取得する場合（標準では無い）、平成１年は平成元年

```
"use strict"

function GetEraYear(target, start) {
  return ((target - start) == 1) ? "元" : target - start;
}
function GetFullEraString(year) {
  var result = "";
  if (year > 1988) {
    result = "平成" + GetEraYear(year, 1988) + "年";
  } else if (year > 1925) {
    result = "昭和" + GetEraYear(year, 1925) + "年";
  } else if (year > 1911) {
    result = "大正" + GetEraYear(year, 1911) + "年";
  } else if (year > 1867) {
    result = "明治" + GetEraYear(year, 1867) + "年";
  } else {
    result = year + "年";
  }
  return result;
}
function GetEraString(year) {
  var result = "";
  if (year > 1988) { 
    result = "平成";
  } else if (year > 1925) {
    result = "昭和";
  } else if (year > 1911) {
    result = "大正";
  } else if (year > 1867) {
    result = "明治";
  }
  return result;
}
console.log(GetEraString(2016));
console.log(GetFullEraString(2016));
console.log(GetEraString(1990));
console.log(GetFullEraString(1990));
console.log(GetEraString(1989));
console.log(GetFullEraString(1989));
console.log(GetEraString(1988));
console.log(GetFullEraString(1988));
console.log(GetEraString(1927));
console.log(GetFullEraString(1927));
console.log(GetEraString(1926));
console.log(GetFullEraString(1926));
console.log(GetEraString(1925));
console.log(GetFullEraString(1925));
console.log(GetEraString(1913));
console.log(GetFullEraString(1913));
console.log(GetEraString(1912));
console.log(GetFullEraString(1912));
console.log(GetEraString(1911));
console.log(GetFullEraString(1911));
console.log(GetEraString(1869));
console.log(GetFullEraString(1869));
console.log(GetEraString(1868));
console.log(GetFullEraString(1868));
console.log(GetEraString(1867));
console.log(GetFullEraString(1867));
```

```
Console出力

平成
平成28年
平成
平成2年
平成
平成元年
昭和
昭和63年
昭和
昭和2年
昭和
昭和元年
大正
大正14年
大正
大正2年
大正
大正元年
明治
明治44年
明治
明治2年
明治
明治元年

1867年
```

- 数字　⇔　日付

```
"use strict"

let hoge = new Date();
console.log(hoge);
let fuga = Number(hoge);
console.log(fuga);
let gaga = Date(fuga);
console.log(gaga);
```

```
Console出力

Tue Oct 04 2016 18:40:03 GMT+0900 (東京 (標準時))
1475574003018
Tue Oct 04 2016 18:40:03 GMT+0900 (東京 (標準時))
```

- 文字列　⇔　配列

```
```

---

# 制御構造

- if

```
"use strict"

let hoge = 1;
if (hoge == 1) {
  console.log("1");
} else if (hoge == 2) {
  console.log("2");
} else {
  console.log("other");
}
```

- select/case

```
"use strict"

let hoge = 1;
switch (hoge) {
  case 1:
    console.log("1");
    break;
  case 2:
  case 3:
    console.log("2 or 3");
    break;
  default:
    console.log("other");
    break;
}

let fuga = "0";
switch (fuga) {
  case 0:
    console.log("0");
    break;
  case "0":
    console.log('"0"');
    break;
  default:
    console.log("other");
    break;
}
```

- for

```
"use strict"

for (let loopcount = 0; loopcount < 10; loopcount++) {
	console.log(loopcount);
}

for (let x = 0, y = 0; x < 10; x++, y += 2) {
  console.log(x);
  console.log(y);
}

for (let loopcount = 0; loopcount < 10; loopcount++) {
  if (loopcount === 8) {
    break;
  }
  console.log(loopcount);
}

for (let loopcount = 0; loopcount < 10; loopcount++) {
  if (loopcount === 8) {
    continue;
  }
  console.log(loopcount);
}
```

```
Console出力

0
1
2
3
4
5
6
7
8
9
0
0
1
2
2
4
3
6
4
8
5
10
6
12
7
14
8
16
9
18
0
1
2
3
4
5
6
7
0
1
2
3
4
5
6
7
9
```

- while/do while

```
"use strict"

let hoge = 0;
while (hoge < 10) {
	console.log(hoge++);
}

let fuga = 0;
do {
	console.log(fuga++);
} while (fuga < 10)
```

```
Console出力

0
1
2
3
4
5
6
7
8
9
0
1
2
3
4
5
6
7
8
9
```

- for in

```
"use strict"

let hoge = {x: 'a', y: 'b', z: 'c'};
for (let fuga in hoge) {
  console.log(fuga);
}
```

```
Console出力
x
y
z
```

- for of

```
"use strict"

let hoge = ['a', 'b', 'c'];
for (let fuga of hoge) {
	console.log(fuga);
}
```

```
Console出力

a
b
c
```

- 可変長引数

```
```

---

# 比較演算子

```
// --
// !=
// <
// <=
// >
// >=
// ===
// !==

```

# 論理演算子

```
// &&
// ||
// !
```

# 三項演算子

```
"use strict"

let hoge = 0.1;
let result = (hoge === 0.1 ? "yes" : "no");
console.log(result);
```

```
Console出力

yes
```

---

# 配列
- 配列・連想配列・ハッシュ

```
"use strict"

let hoge = ["a", "b", "c"];
let fuga = {x: "1", y:"2", z:"3"};

console.log("hoge.length = " + hoge.length);
console.log("hoge[0] = " + hoge[0]);
console.log("fuga.x = " + fuga.x);
console.log("fuga['x'] = " + fuga['x']);


```

```
Console出力

hoge.length = 3
hoge[0] = a
fuga.x = 1
fuga['x'] = 1
```

- 分割代入

```
"use strict"

let hoge = ["a", "b", "c", "d"];
let [hoge_a, hoge_b, hoge_c, hoge_d] = hoge;
console.log(hoge_a);
console.log(hoge_b);
console.log(hoge_c);
console.log(hoge_d);

// 分割代入に寄るスワップ
let x = "xxxxx";
let y = "yyyyy";
[x, y] = [y, x];
console.log(x);
console.log(y);

```

```
Console出力

a
b
c
d
yyyy
xxxx
```

- 削除

```
"use strict"

{
// 先頭・削除
let hoge = ["a", "b", "c"];
console.log(hoge);
console.log(hoge.shift());
console.log(hoge.length);
console.log(hoge);
}
console.log("---");
{
// 末尾・削除
let hoge = ["a", "b", "c"];
console.log(hoge);
console.log(hoge.pop());
console.log(hoge.length);
console.log(hoge);
}
console.log("---");
{
// 位置指定・削除
let hoge = ["a", "b", "c"];
let pos = 1;
console.log(hoge);
console.log(hoge.splice(pos, pos));
console.log(hoge.length);
console.log(hoge);
}
console.log("---");
{
// 指定範囲・削除
let hoge = ["a", "b", "c", "d", "e", "f"];
let pos = 3;
let len = 2;
console.log(hoge);
console.log(hoge.splice(pos, len));
console.log(hoge.length);
console.log(hoge);
}
```

```
Console出力

["a", "b", "c"]
a
2
["b", "c"]
---
["a", "b", "c"]
c
2
["a", "b"]
---
["a", "b", "c"]
["b"]
2
["a", "c"]
---
["a", "b", "c", "d", "e", "f"]
["d", "e"]
4
["a", "b", "c", "f"]
```

- 追加


```
"use strict"

{
// 末尾・追加
let hoge = ["a", "b", "c"];
console.log(hoge);
console.log(hoge.push("x"));
console.log(hoge.length);
console.log(hoge);
}
console.log("---");
{
// 先頭・追加
let hoge = ["a", "b", "c"];
let pos = 0;
console.log(hoge);
console.log(hoge.splice(pos, 0, "x"));
console.log(hoge.length);
console.log(hoge);
}
console.log("---");
{
// 指定位置・追加
let hoge = ["a", "b", "c"];
let pos = 1;
console.log(hoge);
console.log(hoge.splice(pos, 0, "x"));
console.log(hoge.length);
console.log(hoge);
}
console.log("---");
{
// 指定位置・範囲置換
let hoge = ["a", "b", "c"];
let pos = 1;
let len = 2;
console.log(hoge);
console.log(hoge.splice(pos, len, "x"));
console.log(hoge.length);
console.log(hoge);
}
console.log("---");
```

```
Console出力

["a", "b", "c"]
4
4
["a", "b", "c", "x"]
---
["a", "b", "c"]
[]
4
["x", "a", "b", "c"]
---
["a", "b", "c"]
[]
4
["a", "x", "b", "c"]
---
["a", "b", "c"]
["b", "c"]
2
["a", "x"]
---
```

- 検索

```
```

- ソート

```
```

- 並び替え

```
```

---

# ペア / タプル

```
```

---

# 標準I/O

- 標準入力

```
```

- 標準出力

```
```

- 標準エラー出力

```
```

---

# ファイルI/O
- ファイルI/O（テキスト）

```
```

- ファイルI/O（バイナリ）

```
```

- ファイルシステム操作

```
```


```
ファイル属性
```


```
ファイル名
```


ディレクトリ走査
```
```

---

# ロギング

```
```

---

# HTTP/HTTPSクライアント
- GET

```
```

- POST

```
```

- ファイルアップロード

```
```

# HTTP/HTTPSサーバ
- GET

```
```

- POST

```
```

- ファイルアップロード

```
```

---

# ネットワーク
- DNS

```
```

- サーバソケット

```
```

- クライアントソケット

```
```

- ネットワークI/O

```
```

---

# JSON I/O	
- 文字列　⇔　JSONオブジェクト

```
```

---

# エラーハンドリング

```
"use strict"

let hoge = 1;

try {
  let hibo = hoge / fuga;	
} catch (e) {
  console.log(e);
} finally {
  console.log("done");
}

try {
  throw new Error("エラーです");
} catch (e) {
  console.log(e);
} finally {
  console.log("done");
}
```

```
Console出力

ReferenceError: fuga is not defined(...)
done
Error: エラーです(...)
done
```

---

# オブジェクト指向
- オブジェクト生成

```
```

- オブジェクト破棄

```
```

- 継承

```
```

- インターフェイス

```
```

- リフレクション

```
```

- リフレクション

```
```

---

# 組み込みオブジェクト

- Object
- Function
- Boolean
- Number
- String
- Math
- Date
- RegExp
- Error
- Array
- Map
- WeakMap
- Set
- WeakSet
- Symbol
- Proxy
- Promise
- Global
- JSON

---

# DB接続
- Connect/Disconnect

```
```

- SELECT

```
```

- INSERT

```
```

- UPDATE

```
```

- DELETE

```
```

- ロック

```
```

---

# 暗号化

```
```

---

# 圧縮

```
```

---

# マルチスレッド
- スレッド作成

```
```

- スレッドスリープ

```
```

- スレッド終了

```
```

- スレッド待機

```
```

- 排他制御

```
```

- ロック

```
```

- 非同期処理

```
```

