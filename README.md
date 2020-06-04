# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|password|integer|null: false|
|email|string|null: false|
|first_name|string|null: false|
|last_name|string|null: false|
|first_name_hurigana|string|null: false|
|last_name_hurigana|string|null: false|
|birthday|date|null: false|
### Association
- has_many :items
- has_one :credit
- has_one :delivery_info

## delivery_infosテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|first_name|string|null: false|
|last_name|string|null: false|
|first_name_hurigana|string|null: false|
|last_name_hurigana|string|null: false|
|postal_code|integer|null: false|
|state|string|null: false|
|city|string|null: false|
|street|string|null: false|
|building_name|string|null: false|
|room_number|integer|
|phone_number|integer|

### Association
- has_one :user

## itemsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|name|string|null: false|
|content|text|null: false|
|brand|string|
|status|string|null: false|
|postage|string|null: false|
|prefecture_id|string|null: false|
|shipping_days|string|null: false|
|price|integer|null: false|
|category_id|references|foreign_key: true|
|buyer_id|integer|
### Association
- belongs_to :user
- has_many :images
- belongs_to :category

## categorysテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|ancestry|string|
### Association
- has_many :items
- has_ancestry

## imagesテーブル
|Column|Type|Options|
|------|----|-------|
|item_id|references|null: false, foreign_key: true|
|url|string|null: false|
### Association
- belongs_to :item

## cardsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|card_id|integer|null: false|
|customer_id|integer|null: false|
### Association
- belongs_to :user