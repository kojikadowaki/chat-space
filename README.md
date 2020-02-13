# chatspace

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true|
|mail|string|null: false, unique: true|
|pass|string|null: false, unique: true|

### Association
- has_many :messages
- groups, through: groups_users


## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, unique: true|
|group_id|references|null: false, foreign_key: true|

### Association
- has_many :messages
- users, through: groups_users

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|user_id|references|null: false, unique: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
