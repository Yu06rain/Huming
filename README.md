# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| password           | string | null: false |

### Association

- has_many :tweets
- has_many :originals
- has_many :comments

## originals テーブル

| Column            | Type       | Options     |
| ----------------- | ---------- | ----------- |
| title             | string     | null: false |
| impression        | text       | null: false |
| hardship          | text       | null: false |
| insistence        | text       | null: false |
| period            | string     | null: false |
| language          | string     | null: false |
| website           | text       | null: false |
| environment       | string     | null: false |
| user              | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :comments

## tweets テーブル

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| text             | text       | null: false                    |
| user             | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :comments

## comments テーブル

| Column        | Type       | Options     |
| ------------- | ---------- | ----------- |
| comment       | text       | null: false |
| user          | references | null: false, foreign_key: true |
| tweet         | references | null: false, foreign_key: true |
| original      | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :tweet
- belongs_to :original


## アプリケーション名
Huming

## アプリケーション概要
今回僕が作成するオリジナルアプリは、ツイート機能を実装してプログラマー同士がより繋がりやすく、自分の作ったオリジナルアプリを開発工程を踏まえてweb上に紹介出来るwebアプリケーションサービスです。
具体的に説明すると、自分の作成したオリジナルアプリを完成までの経緯だったり、苦労した点、拘った点、作業期間や、使用した言語、学習に使用したwebサイト等を加えて紹介出来るサービスがあれば自分だけでなく、他人から見てもよりそのアプリケーションの全容が把握しやすくなるのではないかと思いました。

ただオリジナルアプリを紹介出来るだけのサービスであれば利用者数を増やすことは難しいと考えているので、ツイート投稿機能を実装しようと考えています。
オリジナルアプリを日々開発する中で日々の進捗具合や、疑問点などを簡単に呟けるようにしたいと思っています。
ツイート機能を実装することで自分にとっても日々の進捗を簡単に呟くことができ、他人にとってもその人がどんなアプリケーションを作成しようとしているのか把握しやすくなるからです。
またフォロー機能も実装してより開発者同士が繋がりやすくして、日々のオリジナルアプリの開発でお互いのアウトプットや疑問点解決に活かすことが出来るようにしたいと考えております。

また質問機能も実装する予定です。
一人でアプリを開発する上でエラー等が生じても基本的に自力で解決する必要があり、解決までに時間を要することも多々あるかと思います。
そんな時に日々のツイートの延長で簡単に質問出来る機能があれば、一人では大変なオリジナルアプリの開発もある程度緩和されるのではないかと考えました。
日々進捗をツイートしていれば他人から見てもその人が作っているアプリケーションの全体像が把握しやすくなり、結果として回答も得られやすくなると考えています。
既存の質問サイトのようなエラーが起きた部分のみを記載したアバウトな質問はアプリの全体像が把握しづらく、質問側も回答側も使いづらく感じる部分があるので、その点をある程度解消出来るのではないかと考えています。
また既存の質問サイトにはツイート機能などはない為、プログラマー同士が繋がりづらく、質問の回答にも時間がかかり思うような回答が得られないことも多々あるかと思います。
プログラマー同士が繋がりやすい当アプリであれば、開発者同士で質問しやすい環境が出来る為、この課題もある程度解消出来ると考えています。

## URL
デプロイ次第記入

## テスト用アカウント
ログイン機能実装後記入

## 利用方法
TOPページからまずはユーザー登録をする必要があります。
新規登録後から他のユーザーのアプリの紹介やツイートを閲覧出来るようになります。
自分がアプリの紹介を行いたい場合は専用のフォームから必要な情報を記入して投稿出来るようになっています。
質問は質問専用フォームから必要な情報を入力して行うことが出来ます。
またツイート、アプリ紹介文、質問などは編集・削除等も可能です。

## 目指した課題解決

・ペルソナ
このアプリはプログラミングを学び始めた初心者からプログラミングに精通のある中上級者まで自分のアイデアを誰かに共有したい、他のプログラマーと繋がりたいと思う全ての方を対象としています。

年齢層はプログラミングを学んでいる年齢層を考慮し、20代〜40代の男女と指定します。

職業はプログラミングに興味を持っている方全般を対象としている為、特に指定していません。

１、プログラマーが自分で作ったオリジナルアプリを開発工程を踏まえて詳細に公開出来るサービスがあれば便利ではないか
２、プログラマー同士がもっと繋がりやすいアプリケーションがあれば便利ではないか
３、既存の質問サイトはエラーが起こった箇所を部分的に記載して事細かく事情を説明してから質問するのは煩わしく、もっとお手軽に質問出来るサービスがあれば便利ではないか
４、プログラミング学習サイトなどでは得られない、他のプログラマーのオリジナルアプリの開発過程、その中で得た実用的な情報を手軽に見られるサービスがあれば便利ではないか

## 洗い出した要件

ユーザー管理機能、ツイート投稿機能、ツイート一覧表示機能、ツイート詳細表示機能、ツイート情報編集機能、ツイート削除機能、質問投稿機能、質問一覧表示機能、質問詳細表示機能、質問編集機能、質問削除機能、アプリ紹介文投稿機能、アプリ紹介文編集機能、アプリ紹介文詳細表示機能、アプリ紹介文編集機能、アプリ紹介文削除機能、コメント投稿機能、コメント編集機能、コメント削除機能、コード投稿機能、フォロー機能、いいね機能、検索機能

## 実装した機能についての説明
機能実装後記入

## 実装予定の機能
未定

## データベース設計
https://gyazo.com/3669f7da651247c9ae2831f2dd1ec83d

## ローカルでの動作方法
機能実装後記入
