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
|image | text | null: false|
|text | text | null: false|
|user_id | integer | null: false, foreign_key: true|
### Association
- belongs_to :user
- has_many :comments
- has_many :posts_tags
- has_many  :tags,  through:  :posts_tags

## groupテーブル
|Column | Type | Options|
|------ | ---- | -------|
|title | user_id | null: false|
|name | text | foreign_key: true|
### Association
- has_many :posts_tags
- has_many  :posts,  through:  :posts_tags

## groupusersテーブル
|Column | Type | Options|
|------ | ---- | -------|
|user_id | text | null: false|
|user_id | integer | null: false, foreign_key: true|
|group_id | integer | null: false, foreign_key: true|
### Association
- belongs_to :post
- belongs_to :user