# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version 2.3.1

# DB Design

## groups table

|Column|Type|Options|
|------|----|--------|
|name|string|null: false|

### Association
- has_many :members
- has_many :users, through: :members
- has_many :messages

## members table

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## users table

|Column|Type|Options|
|------|----|--------|
|name|string|null: false, index:true|
|mail|string|null: false|

### Association
- has_many :members
- has_many :messages
- has_many :groups, through: :members

## messages table

|Column|Type|Options|
|------|----|--------|
|body|text||
|image|string||
|group_id|references|null: false, foreign_key: true|
|user_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group
