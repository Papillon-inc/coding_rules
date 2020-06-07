# MVVM Guide

[日本語](https://github.com/Papillon-inc/rules/blob/master/mvvm-guide/README.md) | [English](https://github.com/Papillon-inc/rules/blob/master/mvvm-guide/README_en.md)

株式会社Papillonのiosアプリは、このREADMEに記載されているMVVMの方式に則って開発されることとします。

この規約は変更される可能性があります。

## 目次
  - [MVVMとは](##MVVMとは)
  - [MVVMの構成要素](##MVVMの構成要素)
    - [Model](###Model)
    - [View](###View)
    - [ViewModel](###ViewModel)
  - [MVVMの構成](##MVVMの構成)
  - [ディレクトリ構成](##ディレクトリ構成)
    - [Models](###Models)
    - [Navigators](###Navigators)
    - [Utilities](###Utilities)
    - [ViewModels](###ViewModels)
    - [Views](###Views)

---

## MVVMとは
  MVVMは、ユーザーにインターフェースを提供するためのViewと、DBやサーバーと通信の処理を行ったりするModelと、その2つの中間でデータバインディングをするViewModelの3つから構成されるアーキテクチャのことです。
  `RxSwift`と、`RxCocoa`というフレームワークを使います。

  **参考**
  > https://github.com/rockname/ArchitectureSampleWithFirebase/tree/mvvm/ArchitectureSampleWithFirebase

## MVVMの構成要素
  MVVMを構成する3つの要素について説明します。

  ### Model
  DBやサーバーと通信を行います。
  他にも、データ型の定義などを行います。
  ModelからViewModelに、実際に使うデータを受け渡します。
  Modelは、1クラスにつき1責務くらいにしておくのがよいとされています。
  （例：　フレンドリストの受け渡し、ログイン処理の通信）

  ### ViewModel
  ViewとModel間の伝達の役目を持ちます。
  Viewの状態を監視して、例えばボタンならクリックされたときにModelからデータを取得する、というような処理を再現することができます。
  

  ### View
  ViewModelから受け取ったデータを、データバインディングで自動的に描画します。
  1つの画面ごとに1つのViewControllerがあり、それが1つのViewModelと対応しています。
  ViewControllerに配置されているViewで、イベントを発生させたいものを1つのViewModelでまとめて監視します。


## MVVMの構成
この図のような構成をしています。
 <img width="873" alt="image" src="https://user-images.githubusercontent.com/41826375/83253877-b33faa00-a1e8-11ea-97c4-df16199d7e07.png">

ViewModelには、RxSwiftというものを用います。

## ディレクトリ構成
ディレクトリ構成は、以下の通りです。
```
Models/
Navigators/
Utilities/
ViewModels/
Views/
  |- Components/
AppDelegate.swift
Info.plist
```

### Models
モデルのファイル（`AuthModel.swift`）を保管します。

### Navigators
画面遷移を扱う`Navigator`を保管します。

### Utilities
汎用的なクラスを保管します。

### ViewModels
モデルとビューの中間のファイル（`MyAwesomeViewModel.swift`）を保管します。

### Views
ビューのファイル（`MyAwesomeView.swift`）を保管します。

### Views/Components
ボタンやラベルなどの部品を保管します。

---

# 参考
 > [MVVMについて](https://qiita.com/s_emoto/items/b000a5c076f3d6076972)

 > [kickstarter](https://github.com/kickstarter/ios-oss)

 > [MVVMを図にしてみた](http://neutoria.blogspot.com/2011/10/mvvm.html)

 > [アーキテクチャについての記事](https://medium.com/@rockname/clean-archirecture-7be37f34c943)
