# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# テーブル設計
## usersテーブル
| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association
- has_many :room_users
- has_many :messages
- has_many :rooms, through: room_users 

## roomsテーブル
| Colmun | Type   | Options     |
| ------ | ------ | ------------|
| name   | String | null: false |

### Assositation
- has_many :room_users
- has_many :messages
- has_many :users, through: room_users

## room_usersテーブル
| Column | Type       | Options                         |
| ------ | ---------- | ------------------------------- |
| user   | references | null: false, foreign_keys: true |
| room   | references | null: false, foreign_keys: true |

### Associtaion
- belongs_to :user
- belongs_to :room

## messagesテーブル
| Column  | Type       | Options                         |
| ------- | ---------- | ------------------------------- |
| content | string     |                                 |
| user    | references | null: false, foreign_keys: true | 
| room    | references | null: false, foreign_keys: true |

### Association
- belongs_to :user
- belongs_to :room