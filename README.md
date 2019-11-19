# README

## ChatSpaceDB設計

### usersテーブル

| column   | type   | options     |
|----------|--------|-------------|
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |

#### Assosiation
has_many :messages  
has_many :users, through: :groups_users


### groupsテーブル

| column  | type       | options                        |
|---------|------------|--------------------------------|
| name    | string     | null: false                    |
| user_id | integer    | null: false, foregin_key: true |

#### Assosiation
has_many :messages  
has_many :users, through: :groups_users


### users_groupsテーブル

| column   | type       | options                        |
|----------|------------|--------------------------------|
| user_id  | integer    | null: false, foregin_key: true |
| group_id | integer    | null: false, foregin_key: true |

#### Assosiation
belongs_to :users  
belongs_to :groups


### messagesテーブル

| column   | type       | options                        |
|----------|------------|--------------------------------|
| body     | text       | null: false                    |
| image    | string     | null: false                    |
| group_id | integer    | null: false, foregin_key: true |
| user_id  | integer    | null: false, foregin_key: true |

#### Assosiation
belongs_to :user  
belongs_to :group
