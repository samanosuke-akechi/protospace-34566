# アプリケーション概要
TECH CAMPの実装課題として実装したアプリケーション。  
基礎・応用・発展カリキュラムで学んだことを駆使して、具体的な作業内容なしで、大まかに「ユーザー管理機能を実装しよう」「新規登録できるようにしましょう」などといった指示のみで自力で実装を行った。  
最終的にHerokuでデプロイして、TECH CAMPの人に機能が実装できているかの確認をしてもらうといった課題だった。  
アプリケーションの機能としては、ユーザー管理機能（新規登録・ログイン・ログアウト機能）、投稿機能（投稿・編集・削除機能、画像投稿）、コメント機能がある。  
画像投稿はActiveStorageで実装している。Herokuの仕様として画像は時間が経つとリンク切れする。  
https://protospace-34566.herokuapp.com/

# テーブル設計

## users テーブル
| Column     | Type    | Options     |
| ---------- | ------- | ----------- |
| email      | string  | null: false |
| password   | string  | null: false |
| name       | string  | null: false |
| profile    | text    | null: false |
| occupation | text    | null: false |
| position   | text    | null: false |

### Association

- has_many :prototypes
- has_many :comments

## prototypes テーブル
| Column     | Type      | Options                        |
| ---------- | --------- | ------------------------------ |
| title      | string    | null: false                    |
| catch_copy | text      | null: false                    |
| concept    | text      | null: false                    |
| user       | refernces | null: false, foreign_key: true |

### Association

- belongs_to :user
- has-many   :comments

## comments テーブル
| Column     | Type       | Options                        |
| ---------- | ---------- | ------------------------------ |
| text       | text       | null] false                    |
| user       | references | null: false, foreign_key: true |
| prototype  | references | null: false, foreign-key: true |

### Association
- belongs_to :user
- belongs_to :prototype