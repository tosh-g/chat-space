# chat-space

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false, unique: true, add_index|
|name|string|null: false|
|group_id|integer|null: false, foreign_key: true|

### Association
- has_many :message
- has_many :groups, through: :members



## groupesテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index|
|user_id|integer|null: false, foreign_key: true|

### Association
- has_many :messages
- has_many :users, through: :members



## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user



## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
