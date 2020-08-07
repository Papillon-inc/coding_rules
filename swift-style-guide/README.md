# Swift Style Guide

[日本語](https://github.com/Papillon-inc/coding_rules/blob/master/swift-style-guide/README.md) | [English](https://github.com/Papillon-inc/coding_rules/blob/master/swift-style-guide/README_en.md)

株式会社Papillonでは、このREADMEに記載されているコーディング規約に従ってSwiftのコードを書いていくこととします。

このコーディング規約は変更される可能性があります。



## 目次
 - [ソースファイル](##ソースファイル)
    - [ファイル名の付け方](###ファイル名の付け方)
    - [ファイル構成](###ファイル構成)
    - [インデントサイズ](###インデントサイズ)
    - [フォーマット](###フォーマット)
    - [括弧](###括弧)
    - [イニシャライザ](###イニシャライザ)
    - [条件分岐](###条件分岐)
 - [命名](##命名)
    - [大文字・小文字](###大文字・小文字)
    - [名前の付け方](###名前の付け方)
 - [ベストプラクティス](##ベストプラクティス)
    - [コメント](###コメント)
    - [ダイナミックと安全性](###ダイナミックと安全性)
    - [アクセス修飾子](###アクセス修飾子)
    - [型推論](###型推論)
 - [ディレクトリ構成](##ディレクトリ構成)



---



## ソースファイル
ソースファイルにおいて、どのようにコードを記述すればよいかについて説明します。



### ファイル名の付け方
   - クラス名は、`JohnLennon`のように**PascalCase**で付けましょう。
   - 単なるクラス`JohnLennon`のみを含むファイルは、`JohnLennon.swift`と名付けましょう。
   - Protocolの`Singable`のみを実装しているクラス`JohnLennon`を含むファイルは、`JohnLennon+Singable.swift`と名づけるようにしましょう。



### ファイル構成
   ファイルの中身は、
   `ファイルコメント`
   `import宣言`
   `型、変数、関数宣言`
   `オーバーロードされた関数`
   `Extension`
   の順番で記述していくものとします。



### インデントサイズ
   インデントのサイズは、**スペース2個**とします。
   タブではなくスペース2個です。
   Xcodeのタブのスペース数設定をスペース2つに設定しておくことをおすすめします。



### フォーマット
   - 文末にセミコロン（`;`）は付けないようにしましょう。
   - メソッドとメソッドの間に一行以上の空行を入れるようにしましょう。
   - `+`や`-`のような演算子の周りには、半角スペースを1つ入れるようにしましょう。
   - ソースファイルの一番最後の行に空行を一行だけ入れるようにしましょう。
   - コンマ（`,`）の前にはスペースを入れず、後ろには半角スペースを一つ入れるか、新しい行にするようにしましょう。
   - 型を示すコロン（`:`）の前にはスペースを入れず、後ろには半角スペースを入れるようにしましょう。
   - `case`文のコロン（`:`）は前に半角スペースを入れず、後ろには半角スペースを一つ入れるか、新しい行にするようにしましょう。
   - 型の宣言をした部分は、後ろに一行以上の空行をいれるようにしましょう。



### 括弧
   - クラスの始めカモメ括弧（`{`）の後ろは、1行空行を入れましょう。
   - 始めカモメ括弧（`{`）は、前の文字との間に半角スペースを1つ入れるようにしましょう。
   - 終わりカモメ括弧（`}`）が対の始めカモメ括弧（`{`）と違う行にある場合、終わりカモメ括弧（`}`）は宣言部分の左端に揃えるようにしましょう。



### イニシャライザ
   イニシャライザの引数では、原則的に名前付き引数を使うのは避けましょう。

```swift
public struct Person {

   public let name: String
   public let phoneNumber: String

   // GOOD.
   public init(name: String, phoneNumber: String) {
      name = name
      phoneNumber = phoneNumber
   }
}
```
```swift
public struct Person {

   public let name: String
   public let phoneNumber: String

   // AVOID.
   public init(name otherName: String, phoneNumber otherPhoneNumber: String) {
      name = otherName
      phoneNumber = otherPhoneNumber
   }
}
```



### 条件分岐
   - `if`、`else`、`switch`、`do`、`catch`、`repeat`、`guard`、`for`、`while`、`defer`文は、対になっている終わりカモメ括弧（`}`）と左端に揃えるようにしましょう。
   - できる限りネストを避け、早い段階で`return`する。
   - `if`、`switch`、`for`、`while`文の条件式は丸括弧（`()`）で囲まないようにしましょう。



## 命名
変数や関数などに名前を付けるときのルールについてです。



### 大文字・小文字
   - `class`、`struct`、`enum`、`protocol`の型の名前は**PascalCase**で付けましょう。
   - `enum`と`OptionSetType`の値も**PascalCase**で付けるようにしましょう。
   - 変数名と関数名は**camelCase**で付けましょう。
   - `URLString`のような、頭文字語が含まれている場合はその頭文字語を**UPPERCASE**としましょう。



### 名前の付け方
   - 1文字の名前を型、変数、関数に付けないようにしましょう。
   - `i`などの、イテレータのインデックスの場所のみ、1文字の変数を使ってもいいことにします。
   - できる限り省略した名前ではなく、くわしい名前を付けるようにしましょう。
   - 名前はそれが何であるか、何のためであるかをできる限り表すものを付けるようにしましょう。
   - `URL`に限っては、型が文字列なのか`NSURL`なのかを区別するために、文字列である場合には`~String`を名前の末尾に付けるようにしましょう。
   - `class`、`struct`、`enum`、`protocol`など、冗長な接尾辞を名前に含めないようにしましょう。



## ベストプラクティス
コードをより良くするためのベストプラクティスについて説明します。



### コメント
   - `//`の後ろには半角スペースを1つ入れるようにしましょう。
   - アノテーションコメントを活用するようにしましょう。
   - 極力コメントを書かなくて済むような、説明的な名前を付けるようにしましょう。
   - コードを見てすぐわかるようなことにコメントは付けないようにしましょう。



### ダイナミックと安全性
   - Objective-Cの`protocol`の実装部分は、`@objc dynamic`を最初に付けるようにしましょう。
   - `IBAction`と`IBOutlet`は`dynamic`を付けるようにしましょう。
   - `@IBOutlet`は`weak`で宣言して、型は`ImplicitlyUnwrappedOptional(!)`ではなく、`Optional(?)`とするようにしましょう。



### アクセス修飾子
   - `private`として宣言することをデフォルトとして、必要なときだけ`internal`、または`public`として外部に公開するようにしましょう。
   - アクセス修飾子は、`@`以外の修飾子の前に付けるようにしましょう。



### 型推論
   - 必要な場合を除いて、変数やプロパティの型は宣言文の左側か右側のいずれか片側から推測できるようにする。

```swift
// GOOD.
var lineBreakMode = NSLineBreakMode.ByWordWrapping
// or
var lineBreakMode: NSLineBreakMode = .ByWordWrapping
```
```swift
// AVOID.
var lineBreakMode: NSLineBreakMode = NSLineBreakMode.ByWordWrapping
```



## ディレクトリ構成
   ディレクトリ構成は、MVVMのOSSの[kickstarter](https://github.com/kickstarter/ios-oss)を参考にします。



---



# 参考:
 > [eureka Swift Style Guide](https://github.com/eure/swift-style-guide/blob/master/README_jp.md#%E3%83%80%E3%82%A4%E3%83%8A%E3%83%9F%E3%83%83%E3%82%AF%E3%81%A8%E5%AE%89%E5%85%A8%E6%80%A7)

 > [Swift Style Guide](https://google.github.io/swift/#identifiers)

 > [kickstarter](https://github.com/kickstarter/ios-oss)
