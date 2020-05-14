# README

# chat-space DB設計

## usersテーブル
|Colum|Type|Options|
|-----|----|-------|
|name|string|null: false, index: :true|
### Association
- has_many :groups
- has_many :messages

## groupsテーブル
|Colum|Type|Options|
|-----|----|-------|
|name|string|null: false|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- has_many :messages
- has_many :group_users
- has_many :users, through: :group_users

## messagesテーブル
|Colum|Type|Options|
|-----|----|-------|
|body|text||
|image|string||
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to: group

## group_usersテーブル
|Colum|Type|Options|
|-----|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to: group