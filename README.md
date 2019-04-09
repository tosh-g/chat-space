# chat-space

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false, unique: true, index: true|
|name|string|null: false|

### Association
- has_many :message
- has_many :members
- has_many :groups, through: :members



## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index|

### Association
- has_many :messages
- has_many :members
- has_many :users, through: :members



## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user



## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
