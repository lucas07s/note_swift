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
|`var 変数名 = 値`|これから使用する変数の宣言と、最初に入れる値を指定する|`変数名`:値を入れる変数の名前|

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
|`let 定数名 = 値`|これから使用する定数の宣言と、定数に入れる値を指定する|`定数名`:値を入れる定数の名前|

### 例
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
|`var 変数名: データ型 = 値`|これから使用する変数の宣言と、最初に入れる値を指定する|`変数名`:値を入れる変数の名前,<br>`データ型`:変数に代入することができる値の種類|

## 整数を扱うデータ型
|データ型|代入できる値の範囲|
|:-:|:-:|
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
|:-:|---|
|`Float`|32bit浮動小数点|
|`Double`|64bit浮動小数点|

### 例
```swift
var x: Double = 3.14
var y: Float = 1.08

var n1 = 10 // 型推論によりInt型になる。
var n2 = 10.0 // 型推論によりDouble型になる。
```

## 文字を扱うデータ型
|データ型|代入できる値の範囲|
|:-:|---|
|`String`|0文字以上|
|`Character`|1文字のみ|

### 例
```swift
var x: String = "あいうえお"
var y: Character = "あ"
var z: Character = "abc" // <<< Characterは1文字しか代入できないのでエラー。 >>>
var n = "あ" // 型推論を使用した場合はString型になる。
```

## 真偽を扱うデータ型
|データ型|代入できる値の範囲|
|---|---|
|`Bool`|`true`または`false`|

### 例
```swift
var x: bool = true
var y: bool = false
```

---

# 型推論による変数宣言

|書式|概要|パラメーター|
|---|---|---|
|`type(of: 変数名)`|指定した変数のデータ型を文字列で取得する|`変数名`:データ型を調べたい変数|

## 例
```swift
var x = 5
var y = 3.14
var z = "A"

print(type(of: x)) // 「Int」と出力される。
print(type(of: y)) // 「Double」と出力される。
print(type(of: z)) // 「String」と出力される。
```

---

# 値が何もない状態を扱う（オプショナル型を使用）
変数や定数は値を入れずに使うことはできないが、場合によっては値が何もない状態を使用したい場合がある。
この値が何もない状態のことをSwiftでは`nil（ニル）`と呼ぶ。
nilを使用したい場合はデータ型の後ろに`?`をつけたオプショナル型というデータ型を使用する必要がある。

## オプショナル型の変数宣言
|書式|概要|パラメーター|
|---|---|---|
|`var 変数名: データ型? = 値`|nilを代入できる変数を宣言する|`変数名`:値を入れる変数名|

### 例
```swift
var suji: Int? = nil
var moji: String? = nil

suji = 3
moji = "データ"

print(suji) // 「3」と出力される
print(moji) // 「データ」と出力される
```

### アンラップ（Unwrap）
オプショナル型変数にnilが入っていないことがわかっている場合は、アンラップ（Unwrap）という処理をして使用することができる。
アンラップをするとオプショナル型ではない、通常の変数として扱われる。
アンラップするにはオプショナル型の後ろに`!`をつける。

#### 例
```swift
var num1 = 2
var num2: Int? = nil

num2 = 3

print(num1 + num2!) // num2をアンラップして通常のInt型として扱われるようにしてから足し算しているため、「5」と表示される。
```

---

# 四則演算
Swiftで計算をするときに使用する演算子は下記の通り。
|数学などで使う記号|演算子|説明|
|:-:|:-:|---|
|+|+|足し算を行う|
|-|-|引き算を行う|
|*|×|掛け算を行う|
|/|÷|割り算をして商を求める|
|%|÷|割り算をして余りを求める|

## 例
```swift
let ans1 = 1 + 2
let ans2 = 2 - 3
let ans3 = 4 * 2
let ans4 = 7 / 3
let ans5 = 7 % 3

print(ans1) // 「3」と出力される。
print(ans2) // 「-1」と出力される。
print(ans3) // 「8」と出力される。
print(ans4) // 「2」と出力される。
print(ans5) // 「1」と出力される。
```

print命令のカッコの中に直接計算式を書くこともできる。
```swift
print(1 + 2) // 「3」と出力される。
print(2 - 3) // 「-1」と出力される。
print(4 * 2) // 「8」と出力される。
print(7 / 3) // 「2」と出力される。
print(7 % 3) // 「1」と出力される。
```

## 演算子を使う際の注意
演算子の前後に半角スペースを入れることができるが、演算子の前後どちらかにのみスペースを入れることはできない。

### 例
```swift
let ans1 = 5 + 1
let ans2 = 5+1
let ans3 = 5+ 1 // <<< 演算子の前にスペースがない（または演算子の後にスペースがある）ためエラー。 >>>
```

## 複数の演算子を使う
複数の演算子を使用して計算をすることもできる。
始めにカッコ内、掛け算、割り算を計算し、次に左から順に計算を行う。

### 例
```swift
print(1 + 2 + 3) // 「6」と表示される。
print(3 + 2 - 1) // 「4」と表示される。
print(2 * 3 - 1) // 「5」と表示される。
print(1 + 2 * 3) // 「7」と表示される。
print((2 + 7) * (5 + 1)) // 「54」と表示される
```

---
# コメントを記述する
どのような目的で書いたプログラムなのか、わかりやすくするためにコメントを記述する。
## 1行のコメント書式
|書式|概要|
|---|---|
|`// コメント`|1行のコメントを記述する|

### 例
```swift
// 税率設定
let TAX = 1.08

let x = 120 * TAX // 120円の税込金額を求める
```

## 複数行のコメント書式
|書式|概要|
|---|---|
|`/* コメント ... コメント */`|複数行のコメントを記述する|

### 例
```swift
/* =============================================
# リポジトリ lucas07s/note-swift #
	URL: https://github.com/lucas07s/note-swift/
============================================= */
```

---

# 比較演算子
|演算子|説明|使用例|
|:-:|---|:-:|
|==|左の値が右の値と等しい場合はtrue、そうでなければfalse|x == y|
|!=|左の値が右の値と等しくない場合はtrue、そうでなければfalse|x != y|
|<|左の値が右の値より小さい場合はtrue、そうでなければfalse|x < y|
|>|左の値が右の値より大きい場合はtrue、そうでなければfalse|x > y|
|<=|左の値が右の値以下場合はtrue、そうでなければfalse|x <= y|
|>=|左の値が右の値以上場合はtrue、そうでなければfalse|x >= y|

## 例
```swift
let x = 2
let y = 3

print(x == y) // false
print(x != y) //true
print(x < y) // true
print(x > y) // false
print(x <= y) // true
print(x >= y) // false
```

---

# 条件分岐
「もし〇〇ならば」というような条件分岐はif文を使用して表現します。

## if文の書式①
|書式|概要|パラメーター|
|---|---|---|
|`if 条件式 { 条件式が満たされた場合の処理 }`|条件式が満たされた場合の処理を実行する|`条件式`:結果が`true`か`false`となる式|

### 例
```swift
let weight = 64.5 // 体重（kg）
let height = 1.6 // 身長（m）
let bmi = weight / (height * height) // BMIを計算

if bmi < 25 /* BMIが25未満なら〜 */ {
  print("肥満度指数は標準未満です。")
}
```

## if文の書式②

|書式|概要|パラメーター|
|---|---|---|
|`if 条件式 { 条件式が満たされた場合の処理 } else { 条件が満たされなかった（そうでない）場合の処理 }`|条件式が満たされた場合の処理、または満たされなかった場合の処理を実行する|`条件式`:結果が`true`か`false`となる式|

### 例
```swift
let weight = 64.5 // 体重（kg）
let height = 1.6 // 身長（height）
let bmi = weight / (height * height) // BMIを計算

if bmi < 25 /* BMIが25未満なら〜 */ {
  print("肥満度指数は標準未満です。")
} else /* そうでなければ〜 */ {
  print("肥満度指数は標準以上です。")
}
```

## if文の書式③
|書式|概要|パラメーター|
|---|---|---|
|`if 条件式1 { 条件式1が満たされた場合の処理 } else if 条件式1 { 条件式2が満たされた場合の処理 } else { いずれの条件が満たされなかった（そうでない）場合の処理 }`|複数の条件式のうち、満たされた条件の処理、またはいずれの条件も満たされない場合の処理を実行する<br>elseは省略することも可能です。|`条件式`:結果が`true`か`false`となる式|

### 例
```swift
let weight = 64.5 // 体重（kg）
let height = 1.6 // 身長（height）
let bmi = weight / (height * height) // BMIを計算

if bmi < 18.5 /* BMIが18.5未満なら〜 */ {
  print("BMI値の結果から痩せ型と判断されました。")
} else if bmi < 25 /* BMIが25未満なら〜 */{
  print("BMI値の結果から普通体重と判断されました。")
} else /* いずれの条件が満たされなかったら〜 */ {
  print("肥満度指数は標準以上です。")
}
```

## if文の書式④
|書式|概要|パラメーター|
|---|---|---|
|`if 条件式1 { if 条件式2 { 条件式1が満たされ、条件式2も満たされた場合の処理 } }`|条件式1が満たされ、かつ条件式2も満たされた場合の処理を実行する|`条件式`:結果が`true`か`false`となる式|

### 例
```swift
let gender = "男性"
let age = 27

if gender == "男性" {
  if age >= 25 {
	print("男性で25歳以上です。")
  }
}
```

## if文の書式⑤
|書式|概要|パラメーター|
|---|---|---|
|`if 条件式1 && 条件式2 { 条件式1と条件式2のどちらも満たされた場合の処理 }`|条件式1と条件式2が満たされた場合の処理を実行する|`条件式`:結果が`true`か`false`となる式|

### 例
```swift
let gender = "男性"
let age = 27

if gender == "男性" && age >= 25 {
	print("男性で25歳以上です。")
}
```

### 論理演算子
|演算子|説明|使用例|
|:-:|---|:-:|
|&&|左の値がtrue、右の値もtrueの場合にtrueとなる<br>それ以外はfalseとなる|x && y|
|\|\||左の値、または右の値のどちらかがtrueの場合にtrueとなる<br>左の値も右の値もfalseの場合はfalseとなる|x \|\| y|
|!|値がtrueの場合はfalse、値がfalseの場合はtrueとなる|!x|

---

# switch文
複数の値で条件を分けたいときに、if文を使うとコードがとても長くなってしまい見づらくなってしまう場合がある。
そのため、switch文を使ってあげる。
## 例①
```swift
let yobi = "TUE"
var msg = "？曜日"

switch yobi {
	case "SUN":
		msg = "日曜日"
	case "MON":
		msg = "月曜日"
	case "TUE":
		msg = "火曜日"
	case "WED":
		msg = "水曜日"
	case "THU":
		msg = "木曜日"
	case "FRI":
		msg = "金曜日"
	case "SAT":
		msg = "土曜日"
	default:
		msg = "？"
}

print("今日は\(msg)です") // 「今日は火曜日です」と出力される
```

## 例②
```swift
let yobi = "TUE"
var msg = "？"

switch yobi {
	case "MON", "TUE", "WED", "THU", "FRI":
		msg = "平日"
	case "SUN", "SAT":
		msg = "休日"
	default:
		msg = "？"
}

print("今日は\(msg)です") // 「今日は平日です」と出力される
```

## 範囲演算子
|演算子|説明|使用例|
|:-:|---|:-:|
|...|閉（Closed）範囲演算子<br>演算子の左側の値から右側の値の範囲内かを判定する|1...3<br>（1以上3以下）|
|..<|半開(Half-Open)範囲演算子<br>演算子の左側の値から右側の値未満までの範囲内かを判定する|1..<3<br>（1以上3未満）|

### 例
```swift
let x = 20
var msg = ""

switch x {
	case 4..<12: // 4以上12未満
		msg = "朝です"
	case 12...14: // 12以上14以下
		msg = "昼です"
	case 15...18: // 15以上18以下
		msg = "夕方です"
	case 19...23, 0...3: // 19以上23以下 と 0以上3以下
		msg = "夜です"
	default:
		msg = "不正な値です"
}

print(msg) // 「夜です」と出力される
```

---

# for ~ in文
決められた回数分処理を実行するときはfor ~ in文を使用する。

## for ~ in文の書式①
|書式|概要|パラメーター|
|---|---|---|
|`for 変数 in 繰り返しの範囲 { 繰り返し実行する処理 }`|「繰り返しの範囲」で指定された範囲の分、繰り返し処理を実行する|`変数`:繰り返し範囲の現在の値|

### 例①
```swift
/* ==============================
 # 10回繰り返す処理
============================== */
var x = 0

for i in 1...10 {
	x += i
	print(x)
}

/* ==============================
 # 表示結果
	1
	3
	6
	10
	15
	21
	28
	36
	45
	55
============================== */
```

### 例②
```swift
/* ==============================
 # 10回繰り返す処理
============================== */
var x = 0

for _ in 1...10 {
	x += 1
	print(x)
}

/* ==============================
 # 表示結果
	1
	2
	3
	4
	5
	6
	7
	8
	9
	10
============================== */
```

> #### 「for 変数名 in ~」　から 「for _ in ~」に変更
> for ~ in文の中で変数を使用していないと「Immutable value '変数名' was never used. ~」と表示されてしまう。
> これは、「for ~ in文のところで書いてある変数は1度も使われていません。」ということを示している。
> for ~ in文のinの左側に書く変数は、繰り返し処理の中で使用しない場合は、実行に影響は与えないがアンダースコア記号（_）を置くというルールがある。

## for ~ in文の書式②
|書式|概要|パラメーター|
|---|---|---|
|`for 変数 in (繰り返しの範囲).reversed() { 繰り返し実行する処理 }`|「繰り返しの範囲」で指定された範囲を、降順で繰り返し処理を実行する|`変数`:繰り返し範囲の現在の値（範囲演算子の大きい値から順にセットされる）|

## while文
指定された条件が満たされている間、繰り返し処理を実行させることができる。

## while文の書式
|書式|概要|
|---|---|
|`while 繰り返し条件式 { 繰り返し実行する処理 }`|繰り返し条件式が満たされている間、処理を繰り返し実行する|

### 例①
```swift
var x = 0

while x < 10 {
	print(x)
	x += 1
}

/* ==============================
 # 表示結果
	1
	2
	3
	4
	5
	6
	7
	8
	9
============================== */
```

### 例②
```swift
var x = 0.0

while x < 10 {
	print(x)
	x += 0.5
}

/* ==============================
 # 表示結果
	0.0
	0.5
	1.0
	1.5
	2.0
	2.5
	3.0
	3.5
	4.0
	4.5
	5.0
	5.5
	6.0
	6.5
	7.0
	7.5
	8.0
	8.5
	9.0
	9.5
============================== */
```

## breakキーワード
while文の途中でbreakキーワードを使用すると、処理を中断してwhile文を抜け出すことができる。
また、breakキーワードはfor ~ in文でも使用可能。

### 例
```swift
var x = 0

while x < 10 {
	print(x)
	x += 1

	if x > 5 {
		break
	}
}

/* ==============================
 # 表示結果
	0
	1
	2
	3
	4
	5
============================== */
```

## repeat-while文
repeat-while文を使用すると、処理を実行した後に繰り返すかどうかを判断することができる。

### repeat-while文の書式
|書式|概要|
|---|---|
|`repeat { 繰り返し実行する処理 } while 条件式`|最初に{ ~ }の中を実行し、条件式が満たされている場合は繰り返し実行する|

#### 例
```swift
var x = 0

repeat {
	print(x)
	x += 1
} while x < 10

/* ==============================
 # 表示結果
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
============================== */
```

## ループの入れ子
繰り返し処理を入れ子にすると、はじめに内側の繰り返し処理を完了させ、次に外側の繰り返し処理に戻る。

### 例
```swift
for x in 1...9 {
	for y in 1...9 {
		print("\(x)x\(y)=\(x * y)")
	}
}
```
<details>
	<summary>表示結果</summary>

	```swift
	/* ==============================
	# 表示結果
		1x1=1
		1x2=2
		1x3=3
		1x4=4
		1x5=5
		1x6=6
		1x7=7
		1x8=8
		1x9=9
		2x1=2
		2x2=4
		2x3=6
		2x4=8
		2x5=10
		2x6=12
		2x7=14
		2x8=16
		2x9=18
		3x1=3
		3x2=6
		3x3=9
		3x4=12
		3x5=15
		3x6=18
		3x7=21
		3x8=24
		3x9=27
		4x1=4
		4x2=8
		4x3=12
		4x4=16
		4x5=20
		4x6=24
		4x7=28
		4x8=32
		4x9=36
		5x1=5
		5x2=10
		5x3=15
		5x4=20
		5x5=25
		5x6=30
		5x7=35
		5x8=40
		5x9=45
		6x1=6
		6x2=12
		6x3=18
		6x4=24
		6x5=30
		6x6=36
		6x7=42
		6x8=48
		6x9=54
		7x1=7
		7x2=14
		7x3=21
		7x4=28
		7x5=35
		7x6=42
		7x7=49
		7x8=56
		7x9=63
		8x1=8
		8x2=16
		8x3=24
		8x4=32
		8x5=40
		8x6=48
		8x7=56
		8x8=64
		8x9=72
		9x1=9
		9x2=18
		9x3=27
		9x4=36
		9x5=45
		9x6=54
		9x7=63
		9x8=72
		9x9=81
	============================== */
	```

</details>

---

# コレクション
複数の値を入れることができる変数のことをコレクションと呼ぶ。

## 配列を使った書式
|書式|概要|パラメーター|
|---|---|---|
|`let 配列名 = [要素1, 要素2, 要素3...]`<br>`let 配列名: [データ型] = [要素1, 要素2、要素3...]`|これから使用する配列の宣言と、最初に入れる要素を指定する。<br>要素は[]の中にカンマ（,）で区切って必要な分だけ入れることができる|`配列名`:要素を入れる配列の名前,<br>`要素n`:配列に入れるデータ|
> let ではなく var で宣言しても構わない

### 例①
```swift
// 配列の宣言
let fruit = ["リンゴ", "ミカン", "バナナ"]
let suji = [1, 2, 3, 4, 5]

// 要素を取得して表示
print(fruit[0]) // 「リンゴ」を取り出して表示
print(fruit[2]) // 「バナナ」を取り出して表示
print(suji[2]) // 「3」を取り出して表示
print(suji[5]) // <<< 要素番号が5の要素は存在しないのでエラー。 >>>

// 要素数を取得する
let fruitCount = fruit.count
let sujiCount = suji.count
// 要素数を表示
print("fruitの要素数は\(fruitCount)個です。") // fruitの要素数は3個です
print("sujiの要素数は\(sujiCount)個です。") // sujiの要素数は5個です。
```

### 例②
```swift
// 配列の宣言
var fruit = ["リンゴ", "ミカン", "バナナ"] // 書き換えができるようにvarで宣言

// 変更前の値を表示
print(fruit[1])
// 「ミカン」を「イチゴ」に変更
fruit[1] = "イチゴ"
// 変更後の値を表示
print(fruit[1])
```

## 配列要素の追加の書式
|書式|概要|パラメーター|
|---|---|---|
|`配列名.append(追加する要素)`|配列の最後に要素を追加する|`追加する要素`:配列の最後に追加する要素|

### 例
```swift
var fruit = ["リンゴ", "ミカン", "バナナ"]

// 配列の最後に「イチゴ」を追加
fruit.append("イチゴ")
// fruitの全要素を表示
print(fruit) // 「["リンゴ", "ミカン", "バナナ", "イチゴ"]」と表示される
```

## 配列要素の挿入の書式
|書式|概要|パラメーター|
|---|---|---|
|`配列名.insert(挿入する要素, at: 挿入位置の要素番号)`|配列の途中に要素を挿入する|`挿入する要素`:配列の途中に挿入する要素,<br>`挿入位置の要素番号`:要素を挿入する位置の要素番号|

### 例
```swift
var fruit = ["リンゴ", "ミカン", "バナナ"]

// 配列の要素番号1の場所に「ブドウ」を挿入
fruit.insert("ブドウ", at: 1)
// fruitの全要素を表示
print(fruit) // ["リンゴ", "ブドウ", "ミカン", "バナナ"]と表示される
```

## 配列要素の削除
|書式|概要|パラメーター|
|:-:|---|---|
|`配列名.removeAll()`|配列のすべての要素を削除する||
|`配列名.removeLast()`|配列の最後の要素を削除する||
|`配列名.remove(at: 削除位置の要素番号)`|配列の途中に要素を挿入する|`削除位置の要素番号`:要素を削除する位置の要素番号|

### 例
```swift
var fruit = ["リンゴ", "ミカン", "バナナ"]

fruit.removeLast() // 「バナナ」を削除
print(fruit.count) // 要素数「2」が表示される

fruit.remove(at: 1) // 「ミカン」を削除
print(fruit.count) // 要素数「1」が表示される

fruit.removeAll() // 全ての要素を削除する
print(fruit.count) // 要素数「0」が表示される
```

---

# 辞書（Dictionary）
## 辞書の書式
|書式|概要|パラメータ|
|---|---|---|
|`let 辞書名 = [キー1:値1, キー2:値2, キー3:値3, ...]`<br>`let 辞書名:[キーのデータ型:値のデータ型] = [キー1:値1, キー2:値2, キー3:値3, ...]`|使用する辞書の宣言と最初に入れるキーと値を指定する<br>キーと値のペアは[]の中にカンマ（,）で区切って必要な分だけ入れることができる|`辞書名`:キーと値のペアを入れる辞書の名前,<br>`キーn:値n`:辞書に入れるキーと値のペア|
> letではなくvarで宣言しても構わない

### 例
```swift
var fruit = ["リンゴ": 100, "ミカン": 50, "バナナ": 180]
var award = [1: "アカデミー賞", 2: "ノーベル賞", 3: "芥川賞"]

fruit["ブドウ"] = 250
fruit["スイカ"] = 980
award[4] = "グラミー賞"
```

## 辞書の要素の削除
|書式|概要|パラメーター|
|:-:|---|---|
|`辞書名.removeValue(forKey: キー)`|指定したキーの要素を削除|`キー`:削除したい要素のキー|
|`辞書名.removeAll()`|全ての要素を削除する||

### 例
```swift
var fruit = ["リンゴ": 100, "ミカン":50 , "バナナ":180]
var award = [1: "アカデミー賞", 2: "ノーベル賞", 3: "芥川賞"]

fruit.removeValue(forKey: "ミカン")
award.removeAll()
print(fruit) // 「["リンゴ": 100, "バナナ": 180]」が表示される
print(award) // 「[:]」が表示される
```

# 繰り返し処理でコレクションにデータを格納
swiftではからの配列を作成して後から要素を追加することもできる。

## 空の配列の宣言書式
|書式|概要|
|---|---|
|`var 配列名:[データ型] = []`|配列をからの状態で宣言する|

### 例
```swift
var suji:[Int] = []

for i in 1...50 {
	suji.append(i)
}
print(suji)

/*　==============================
　# 表示結果
	[
		1,2, 3, 4, 5,
		6, 7, 8, 9, 10,
		11, 12, 13, 14, 15,
		16, 17, 18, 19, 20,
		21, 22, 23, 24, 25,
		26, 27, 28, 29, 30,
		31, 32, 33, 34, 35,
		36, 37, 38, 39, 40,
		41, 42, 43, 44, 45,
		46, 47, 48, 49, 50
	]
	※ データ5個おきに改行済
============================== */
```

---

# 繰り返し処理でコレクションからデータを取り出す
for ~ in文で以下の書式を使用すると、コレクションから全ての値を1つずつ取り出すことができる。

## コレクションデータの取得の書式
|書式|概要|パラメータ|
|---|---|---|
|`for 変数 in コレクション { 繰り返し実行する処理 }`|コレクションから全ての要素を1つずつ取り出す|`コレクション`:値の取得元,<br>`変数`:コレクションから取り出した値を格納する変数|

### 例
```swift
var suji:[Int] = []

// 50個の値を格納
for i in 1...50 {
	suji.append(i)
}

// sujiから全ての値を取り出して表示する
for atai in suji {
	print(atai)
}
```

<details>
	<summary>表示結果</summary>

	```swift
	/*　==============================
	　# 表示結果
		1
		2
		3
		4
		5
		6
		7
		8
		9
		10
		11
		12
		13
		14
		15
		16
		17
		18
		19
		20
		21
		22
		23
		24
		25
		26
		27
		28
		29
		30
		31
		32
		33
		34
		35
		36
		37
		38
		39
		40
		41
		42
		43
		44
		45
		46
		47
		48
		49
		50
	============================== */
	```
</details>

# 繰り返し間隔の指定
変数の値が間隔で指定した値ずつ増やしながら繰り返し処理をすることができる。

## 繰り返し間隔の指定の書式
|書式|
|---|
|`for 変数 in stride(from: 開始値, to: 終了値, by: 間隔) { 繰り返しで実行する処理 }`|

### 例
```swift
for x in stride (from: 1, to: 10, by: 3) {
	print(x)
}

/* ==============================
 # 表示結果
	1
	4
	7
============================== */
```

# 関数
何度も同じ処理を行う場合は関数で処理をまとめる方法もある。

## 関数の書式
|書式|概要|
|---|---|
|`func 関数名([引数1: データ型1 = 初期値1, 引数2: データ型2 = 初期値2...] {処理}`|引数を受けとって{ ~ }の中を実行する|

### 例
```swift
func getTraiangleArea(base: Double = 0, height: Double = 0) {
	let area = base * height / 2.0
	print("\(base) × \(height) ÷ 2 = \(area)")
}

getTraiangleArea(base: 3, height: 6) // 「3.0 × 6.0 ÷ 2 = 9.0」が表示される

getTraiangleArea(base: 2, height: 5) // 「2.0 × 5.0 ÷ 2 = 5.0」が表示される

getTraiangleArea() // 引数の両方とも初期値を使用しているため「0.0 × 0.0 ÷ 2 = 0.0」と表示される
```

## 戻り値のある関数の書式
|書式|概要|
|---|---|
|`func 関数名() -> 戻り値の型 {処理  return 戻り値}`|{~}の中を実行し、呼び出し元に値を返す関数を定義する|

### 例
```swift
func getTraiangleArea(base: Double, height: Double) -> Double {
	// 受け取った引数から三角形の面積を求める
	let area = base * height / 2.0

	return area
}

// 作成した関数で面積を求める
let area = getTraiangleArea(base: 3, height: 5)
// 求めた面積を表示
print("面積は\(area)です") // 「面積は7.5です」が表示される
```

> ## 関数の引数名を省略するには
> 関数を定義するときに引数名の先頭に「_」を記述する。
> 上記の例と同じ内容で例を作成。
> ### 例
> ```swift
>func getTraiangleArea(_ base: Double, _ height: Double) -> Double {
>	// 受け取った引数から三角形の面積を求める
>	let area = base * height / 2.0
>
>	return area
>}
>
>// 作成した関数で面積を求める
>let area = getTraiangleArea(3, 5) // 引数名省略
>// 求めた面積を表示
>print("面積は\(area)です") // 「面積は7.5です」が表示される
>```

# guard文
## guard文の書式
|書式|概要|
|---|---|
|`guard 条件式 else {条件式がfalseの場合の処理}`|関数を継続する条件が満たされない場合は、関数を終了する処理を実行する|

### 例１
```swift
func getNum(x: Int, y: Int) -> Int {
	// 引数yの値が0以外の場合はgetNum関数の処理を継続する
	guard y != 0 else {
		return 0
	}
	return x / y
}

let ans = getNum(10, y: 0)

print(ans) // 「0」と表示される
```

### 例2
```swift
func printMsg(msg: String?) {
    guard let myMsg = msg else { // msg引数がnilでないかをチェック
        print("nilです")
        return
    }
    print(myMsg)
}

printMsg(msg: "Hello!") // 「Hello!」と表示される

printMsg(msg: nil) // 「nilです」と表示される
```

# defer文
|書式|概要|
|---|---|
|`defer {関数を修了する前に実行したい処理}`|関数を抜ける直前に実行したい処理を定義する|

## 例
```swift
func calcTax(num: Double) -> Double {
	defer {
		print("計算を終了します")
	}

	guard num > 100 else {
		return 0
	}

	let taxNum = num * 1.08
	return taxNum
}

let num1 = calcTax(num: 30)
print("税込価格 = \(num1)") // 「税込価格 = 0.0」と表示される

let num2 = calcTax(num: 130.0)
print("税込価格 = \(num2)") // 「税込価格 = 140.4」と表示される
```

## ポイント
defer文は関数の中に複数書くことができる。
複数書いた場合は、下から順にdefer文が実行されていく。
