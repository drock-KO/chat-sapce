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
## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|integer|null: false, foreign_key: true|
|group|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, foreign_key: true|
|email|string|null: false, unique: true|
|password|string|null: false, unique: true|
|group|integer|null: false, foreign_key: true|

### Association
- belongs_to :group, dependent: :destroy
- has_many :groups, through: :groups_users
- has_many :messages

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, unique: true|
|user|integer|null: false, foreign_key: true|

### Association
- has_many :users, through: :groups_users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|user|integer|null: false, foreign_key: true|
|text|text|null: false|

### Association
- belongs_to :user, dependent: :destroy
- belongs_to :group