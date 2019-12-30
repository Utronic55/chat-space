
# DB設計

## users table
|Column|Type|Options|
|------|----|-------|
|name|text|index:true,null:false,unique:true|
|mail|text|null:false,unique:true|
|password|text|null:false|
|id|integer|foreign_key: true|
|groups_id|integer|foreign_key: true|

### Association
- has_many :groups,through members
- has_many :messages
- has_many :members

## groups table
|Column|Type|Options|
|------|----|-------|
|group_name|text|index:true,null:false,unique:true|
|id|integer|foreign_key: true|
|users_id|integer|foreign_key: true|

### Association
- has_many :users,through members
- has_many :messages
- has_many :members

## messages table
|Column|Type|Options|
|------|----|-------|
|body|text|index:true,null:false,unique:true|
|image||index:true,null:false,unique:true|
|group_id|integer|foreign_key: true|
|user_id|integer|foreign_key: true|

### Association
- belongs_to:user
- belongs_to:group

## members table
|Column|Type|Options|
|------|----|-------|
|group_id|integer|foreign_key: true|
|user_id|integer|foreign_key: true|

### Association
- belongs_to:user
- belongs_to:group