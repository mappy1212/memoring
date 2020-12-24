## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null:false,unique:true|
|email|string|null:false|
|password|string|null;false|
### Association
has_many :tweets
has_many :comments
has_many :messages
has_many :users_groups
has_many :groups, thorough: :users_groups

## tweetsグループ
|Column|Type|Options|
|------|----|-------|
|content|text|
|image|string|
|user_id|integer|null: false , foreign_key: true|
### Association
belongs_to :user
has_many :comments

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|content|string|
|user_id|integer|null: false , foreign_key: true|
### Association
belongs_to :user
belongs_to :tweet

## messageテーブル
|Column|Type|Options|
|------|----|-------|
|content|string|
|image|string|
|user_id|integer|null: false , foreign_key: true|
|group_id|integer|null: false , foreign_key: true|
### Association
belongs_to :user
belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null:false|
### Association
has_many :message
has_many :users_groups
has_many :users, through: :users_groups

## users_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false|
|group_id|integer|null: false|
### Association
belongs_to :user
belongs_to :group

