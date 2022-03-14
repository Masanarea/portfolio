# URL 一覧  

- **ポートフォリオ (PC専用)**  
サイトURL  
https://www.laravelvueport.link/login  
ポートフォリオ動画(２分)  
インスタURL

- **GitHub**  
https://github.com/Masanarea/portfolio.git

- **Instagram(ポートフォリオ以外の Web アプリ作品投稿、アウトプット用)**  
https://instagram.com/masa_626_/


# アプリケーション概要  
**食べログに特化した SNS アプリです。**



## アプリケーションの制作経緯  
前々からインスタグラムに上げられるような飲食店での食事の写真のみを集めたSNSアプリがあったらいいなという考えから制作しました。インスタグラムのような直感的にわかりやすい機能を実装したり、Google Mapのレビューのように誰でも抵抗感なく気軽にコメントを書ける機能を兼ね備えました。今後も、アプリを使用することで少しでも『この店に行ってみたい！』『この料理美味しそうだなぁ』と少しでも感じてもらえるようなWebアプリに改良していけたらと考えています。現在では、実際に友人に使ってもらった際の感想を参考にして、日々改良を重ねています。
長期的には GoogleMap や インスタグラム での食事関連のもの以上に『この店に行ってみたい！』と思ってもらうことを目標にアプリ制作を続けていけたらと考えています。
アプリの機能面やその数、UI部分はまだまだなのですが、今後もこのアプリの保守・運用を続けて行きたいと思います。


## アプリケーション詳細

こちらのアプリを作成する上で気をつけた事は、以下の３点です。

1. 現場で使われやすいモダンな技術を取り入れる(AWS,Docker等)
1. ページ表示速度で不快感を与えないようにする(0.7秒で初期画面の表示)
1. アプリ制作を通して少しでも開発の流れを理解するよう努める

このアプリには Instagram のような写真投稿、コメント、いいね機能のある SNS ですが、
その他に以下のような特徴のあるアプリです。

- 投稿された写真のダウンロード機能(FileReader API、　FormData API を使用)
- フロント側を Vue.js で作成、 インフラに AWS　を使用する事で　ページ表示速度を高速化
- ページネーション機能 (写真６枚ごと)
- エラーハンドリング機能

## 使用画面のイメージ
![firstTime](https://user-images.githubusercontent.com/93495976/158014699-74fb7ba7-4ab5-4577-af93-be6a95d71ae3.gif)

## 使用技術について

フロントエンドを Vue.js 、 バックエンドをPHP(Laravel)で作成し、   
開発環境にDocker/docker-composeを使用し, CircleCI, AWS等のモダンなインフラ技術を用いて、Webアプリを作成しました。

## AWS 構成図

![AWS-ER](https://user-images.githubusercontent.com/93495976/158013902-1ffd9fab-9069-4fa8-9123-dd0428ea287c.png)

## **ページ表示速度と機能(コメントやいいね機能)の速度を高速化した具体例**

  - **Herokuにデプロイでは遅いので AWS を使用**
  - **フロントエンドに Vue.js(Ajaxによる非同期通信、Ajaxではaxiosを使用)**
SPA導入のデメリットの一つとして、初期ローディングにかかる時間が増えることが挙げられます。ただこのアプリではPageSpeed Insightsによると 0.7秒で初期画面の表示ができているとのことでスコア（パーセンテージ）の方も９３と高いのでこの問題はクリアされていると考えています。
<img width="1440" alt="スクリーンショット 2022-03-14 8 34 39" src="https://user-images.githubusercontent.com/93495976/158084288-5be1822e-ec3a-4b09-bb2b-76cf0af320d8.png">

## **技術選定の基準**
- **バックエンドの言語**  
『学習教材が豊富』なこと、個人開発だけでなく今後業務で使うとなった場合にも『長期的に使用していけるかどうか』、の二点を主に基準としました。
まず『学習教材の豊富さ』についてですが、学習教材が豊富なバックエンドの言語はPHP,Ruby。このうち長期的に使用していけるかどうかについて考えた際にGitHubのフレームワークのスター数、Googleトレンド等を参照するとこの条件に最も当てはまるのは、バックエンド言語だとPHPであり、現在（2022年3月）Laravel-11がリリースされるのが確定していることも含めて、PHPのフレームワークにLaravelを使うことを決めました。尚、バージョンについてですが、アプリ開発を始めた日（2021年12月24日頃）のLTS(Long Term Support)はLaravel6であり、Laravel6の情報量もかなり多いことからLaravel6 でのアプリ開発をしていきました。

- **フロントエンド**  
ページ表示速度を早くするために、 Vue.js、React のどちらかを使うことにしましたが、『学習教材が豊富』 なことと、学習コストを考慮して Vue.js を選びました。
Laravelの公式でもVue.jsの方を採用している事も基準の１つでした。
またVue.js を使うにあたって、Ajaxによる非同期通信では、Laravelのpackage.jsonに標準で記載されているaxios(JavaScriptの外部ライブラリ)を使用しました。

- **インフラ**  
インフラをどうするか考える際に、以下の記事を参考にしました  
https://capeyes.hatenablog.com/entry/2015/04/26/091150  
一部記事の内容を引用すると、あるサイトの表示速度について次のようになったとのこと
  - **Heroku**
トップページのリロードでだいたい2.2秒
  - **AWS × 東京リージョン**
トップページのリロードで1秒未満  
このことからページ表示速度を早くするためにも、Herokuではなく、AWS でアプリをデプロイすることに決定しました






## **具体的なモダンな技術一覧**

  - **Laravel + Vue.js の構成**
  - **開発環境にDocker/docker-composeを使用**
  - **Herokuではなく、AWS でアプリをデプロイ**
  - **Circle CIによるCI/CDパイプラインの構築**

## **使用技術の詳細(バージョンや使用ツール)**
- **フロントエンド**

  - **Vue.js 2.6.14**
  - **JavaScript**
  - **HTML / SCC /**

- **バックエンド**

  - **PHP 7.4.1**
  - **Laravel 6.20.26**
  - **PHPUnit 9.5.16**

- **インフラ**

  - **CircleCi**
  - **Docker 20.10.12 / docker-compose 2.2.3**
  - **nginx 1.18**
  - **mysql 5.7.31**
  - **AWS** ( EC2, ALB, ACM, S3, RDS, Route53, VPC, EIP, IAM )

- **その他使用ツール**
  - Visual Studio Code
  - SourceTree(コマンドでGitを使うこともありましたが、主に SourceTree を使用)
  - Slack
  - GitHub
  - Notion （開発中に参考になった記事を管理）
  - PageSpeed Insights（ページに関する実際のパフォーマンスデータを表示/点数化）

- **GitHub や CircleCi の利用において**
  - master ブランチと feature ブランチの二つを用意して作業を進める
  - 機能を追加する際に Issue を利用
  - feature ブランチ でtestが通らない場合、master ブランチにマージできないように設定
  - CircleCI のテスト結果を Slack に通知




## PHPUnit(各テストについて)

|    テスト    |                      内容                      |
| :--------------: | :--------------------------------------------: |
|      AddCommentApiTest       |                コメントを追加できるかどうかのテスト               |
|      LikeApiTest      |               いいねの追加、いいねの解除、2回同じ写真にいいねしても1回しかいいねがつかないかを確認するテスト              |
|     LoginApiTest      |      登録済みのユーザーでログインできるかどうかのテスト       |
| LogoutApiTest | ログインしたユーザーがログアウトできるかどうかのテスト |
|     RegisterApiTest     |               ユーザー登録できるかどうかのテスト               |
|       UserApiTest       |             ログイン中はユーザー情報（name)を返却し、ログアウトの場合は空文字を返却するかかどうかのテスト             |

# ER 図  
### DB 設計
![er drawio](https://user-images.githubusercontent.com/93495976/158013946-d3934509-480a-40d0-b8b8-f00a99c86fd5.png)


### 各テーブルについて

|    テーブル名    |                      説明                      |
| :--------------: | :--------------------------------------------: |
|      users       |                ユーザー情報                |
|      photos      |               登録した写真情報（12桁のランダムな値をidとして管理）               |
|     comments      |      コメント情報       |
| likes | いいね機能に関する情報 |

## 機能一覧

- **一般ユーザー登録関連**

  - **アカウント新規登録**
  - **ログイン、ログアウト機能**





- **ページネーション機能**
- **写真ダウンロード機能**(FileReader API、　FormData API を使用)

- **ユーザー写真投稿(AWS S3 バケットを使用)**

- **コメント機能**
- **エラーハンドリング機能**(写真６枚ごと)
- **いいね機能** (Vue.js / ajax(axios))

### 機能を実装する際に学習したこと
- **アクセサ**
- **正規表現**



## エラーハンドリング機能

- システムエラー
- バリデーションエラー
- 認証エラー
- Not Found エラー






## 今後の課題
かなり課題が山積みなのですが、優先してこの機能は必要だと考えているものについて次のようなものがあります

- スマートフォンに対応させる
- コメントの編集/削除機能
- コメントで改行/絵文字を使えるようにする
- LINEのグループ機能のようなグループ作成機能

まだまだ課題も多いのですが、一つずつ改善してよりブラッシュアップしていきたく思います。


