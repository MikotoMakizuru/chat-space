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
## usersテーブル
|Column | Type |	Options|
|------ | ---- | -------|
|name | string |index: true, null: false, unique: true|
|Email |	text |null: false, unique: true|
|password | text |	null: false|
### Association
- has_many :groups, through: :users_groups
- has_many :messages
- has_many :users_groups

## messesテーブル
|Column | Type | Options|
|------|----|-------|
|image | text | |
|text | text | |
|user_id | referencse | foreign_key: true|
|group_id | referencse | foreign_key: true |
### Association
- belongs_to :user
- belongs_to :group

## groupテーブル
|Column | Type | Options|
|------ | ---- | -------|
|title | user_id | null: false|
|name | text | foreign_key: true, unique: true|
### Association
- has_many :messes
- has_many  :users, through: :groupusers
- has_many  :groupusers

## groupusersテーブル
|Column | Type | Options|
|------ | ---- | -------|
|user_id | integer | null: false, foreign_key: true|
|group_id | integer | null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user