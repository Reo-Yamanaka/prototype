# DB設計

## Users Table
| Column              | Type         | Option            |
|---------------------|--------------|-------------------|
| name                | string       | null: false       |
| email               | string       | null: false       |
| encrypted_password  | string       | null: false       |

### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages


## Rooms Table
| Column       | Type         | Option            |
|--------------|--------------|-------------------|
| name         | string       | null: false       |

### Association
- has_many :room_users
- has_many :users, through: :room_users
- has_many :messages


## Room_users Table
| Column       |  Type         | Option                          |
|--------------|---------------|---------------------------------|
| user         | references    | null: false, foreign_key: true  |
| room         | references    | null: false, foreign_key: true  |

### Association
- belongs_to :room
- belongs_to :user


## Messages Table
| Column       | Type          | Option                          |
|--------------|---------------|---------------------------------|
| content      | string        |                                 |
| user         | references    | null: false, foreign_key: true  |
| room         | references    | null: false, foreign_key: true  |

### Association
- belongs_to :room
- belongs_to :user