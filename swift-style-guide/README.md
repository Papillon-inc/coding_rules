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
    - [プロパティ](###プロパティ)
    - [条件分岐](###条件分岐)
    - [ディレクトリ構成](###ディレクトリ構成)
 - [命名](##命名)
    - [大文字・小文字](###大文字・小文字)
    - [名前の付け方](###名前の付け方)
 - [ベストプラクティス](##ベストプラクティス)
    - [コメント](##コメント)
    - [ダイナミックと安全性](##ダイナミックと安全性)
    - [型推論](##型推論)

---

## ソースファイル
ソースファイルにおいて、どのようにコードを記述すればよいかについて説明します。

### ファイル名の付け方
 - クラス名は、`MyClass`のように**パスカルケース**で付けましょう。
 - 単なるクラス`MyClass`のみを含むファイルは、`MyClass.swift`と名付けましょう。

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

### フォーマット
   - 文末にセミコロン（`;`）は付けないようにしましょう。
   - メソッドとメソッドの間に一行以上の空行を入れるようにしましょう。
   - `+`や`-`のような演算子の周りには、半角スペースを1つ入れるようにしましょう。
   - ソースファイルの一番最後の行に空行を一行だけ入れるようにしましょう。
   - コンマ（`,`）の前にはスペースを入れず、後ろには半角スペースを一つ入れるか、新しい行にするようにしましょう。
   - 型を示すコロン（`:`）の前にはスペースを入れず、後ろには半角スペースを入れるようにしましょう。
   - `case`文のコロン（`:`）は前に半角スペースを入れず、後ろには半角スペースを一つ入れるか、新しい行にするようにしましょう。
   - 型の宣言をした部分は、後ろに一行以上の空行をいれるようにしましょう。
<table>
<tr><th>OK</th><th>NG</th></tr>
<tr>
<td><pre lang=swift>
class Icon {
   let image: UIImage
   var completion: (() -> Void)

   init(image: UIImage) {
      self.image = image
      self.completion = { [weak self in self?.didComplete()] }

   }

   func doSomething() {

      self.doSomethingElse()
   }

}

</pre></td>
<td><pre lang=swift>
class Icon {
   let image: UIImage
   init(image: UIImage) {
      self.image = image
      self.completion = { [weak self] in print("done"); self?.didComplete() }
   }

   func doSomething() { self.doSomethingElse() }
}
</pre></td>
</tr>
</table>


### 括弧
   - 始めカモメ括弧（`{`）は、前の文字との間に半角スペースを1つ入れるようにしましょう。
   

# 参考:
 > [eureka Swift Style Guide](https://github.com/eure/swift-style-guide/blob/master/README_jp.md#%E3%83%80%E3%82%A4%E3%83%8A%E3%83%9F%E3%83%83%E3%82%AF%E3%81%A8%E5%AE%89%E5%85%A8%E6%80%A7)

 > [Swift Style Guide](https://google.github.io/swift/#identifiers)