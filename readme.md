# 文字列や数値を表示するコード

```swift
print("Hello Swift!!")
print(2020)
```

---

# 変数とは
値を入れる箱のことを変数と呼び、変数に値を入れることを代入と呼ぶ。
変数は代入した後に値を書き換えることができる。

## 変数の宣言
|書式|概要|パラメーター|
|---|---|---|
|`var 変数名 = 値`|これから使用する変数の宣言と、最初に入れる値を指定する|変数名:値を入れる変数の名前|

### 例
```swift
var moji = "Hello Swift!!"
var suji = 1972

print(moji) // 「Hello Swift!!」を表示する
print(suji) // 「1972」を表示する

var ans = suji + 28 // 1972 + 28を計算する
print(ans) // 2000を表示する
```

## 変数の値を書き換える
```swift
var moji = "Hello Swift!!"
var suji = 1972

moji = "Swift is fun!!"
suji = 123

print(moji) // 「Swift is fun!!」を表示
print(suji) // 「123」を表示
```

---

# 定数とは
値を入れる箱のことを定数と呼ぶ。
変数と違い、定数は代入した後に値を書き換えることができない。

## 定数の宣言
|書式|概要|パラメーター|
|---|---|---|
|`let 定数名 = 値`|これから使用する定数の宣言と、定数に入れる値を指定する|定数名:値を入れる定数の名前|

## 例
```swift
let PI = 3.14159
let menseki = 5 * 5 * PI

print(menseki) // 計算で求めた面積を表示

PI = 1.234 // <<< 定数は書き換えることができないためエラーとなる。 >>>
```

---

# データの種類
データの種類のことをデータ型と呼ぶ。
代入の際に意図しないエラーを発生しないためにも、変数にデータ型を指定してあげる。

## データ型の宣言
|書式|概要|パラメーター|
|---|---|---|
|`var 変数名: データ型 = 値`|これから使用する変数の宣言と、最初に入れる値を指定する|変数名:値を入れる変数の名前, データ型:変数に代入することができる値の種類|

## 整数を扱うデータ型
|データ型|代入できる値の範囲|
|---|---|
|`Int8`|-128 ~ 127|
|`Int16`|-32768 ~ 32767|
|`Int32`|-2147483648 ~ 2147483647|
|`Int64`|-9223372036854775808 ~ 9223372036854775807|
|`Int`|32bit環境ではInt32と同じ。64bit環境ではInt64と同じ。|

### 例
```swift
var x: Int16 = 7
var y: Int16 = 32768 // <<< Int16の範囲を超えるのでエラーとなる。 >>>
var z: Int16 = 3.14 // <<< 小数を扱うことができないのでエラーとなる。 >>>
```

## 小数を扱うデータ型
|データ型|代入できる値の範囲|
|---|---|
|Float|32bit浮動小数点|
|Double|64bit浮動小数点|

### 例
```swift
var x: Double = 3.14
var y: Float = 1.08

var n1 = 10 // 型推論によりInt型になる。
var n2 = 10.0 // 型推論によりDouble型になる。
```

## 文字を扱うデータ型
|データ型|代入できる値の範囲|
|---|---|
|String|0文字以上|
|Character|1文字のみ|

### 例
```swift
var x: String = "あいうえお"
var y: Character = "あ"
var z: Character = "abc" // <<< Characterは1文字しか代入できないのでエラー。 >>>
var n = "あ" // 型推論を使用した場合はString型になる
```
