## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text| |
|image|string| |
|user_id|references|null: false,foreign_key: true|
|group_id|references|null: false,foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false,unique: true|
|email|string|null: false,unique: true|

### Association
- has_many :messages
- has_many :group_users
- has_many :group, through: :group_users

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false,unique: true,index|

### Association
- has_many :messages
- has_many :group_users
- has_many :users, through: :group_users
