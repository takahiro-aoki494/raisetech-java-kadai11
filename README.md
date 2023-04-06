# 最終課題概要
タスクの一覧を管理するAPIを作成予定
<br>仕様書は下記です。</br>
https://takahiro-aoki494.github.io/raisetech-java-kadai11/swagger/

## データベース定義
### 出荷テーブル
|カラム名（論理名）   | カラム名（物理名）                |型・桁                        |Nullable                      |その他コメント                 |
|:--------------------|:-------------------------|:-----------------------------|:----------------------------- |:----------------------------- |
| 出荷指示書番号      | shipping_order_number    | varchar(255)                 | No                            | primary key                   |
| 納入予定日          | delivery_date            | date                         | No                            | YYYY-MM-DD形式                |
| 出荷予定日          | estimated_shipping_date  | date                         | No                            | YYYY-MM-DD形式                |
| 検査完了予定日      | inspection_complete_date | date                         | No                            | YYYY-MM-DD形式                |
| 出荷先住所          | shipping_address         | varchar(255)                 | No                            |                             |
| 作成日時            | created_at               | datetime                     | No                            | YYYY-MM-DD HH:MM:SS形式       |
| 更新日時            | updated_at               | datetime                     | No                            | YYYY-MM-DD HH:MM:SS形式       |
### 商品テーブル
|カラム名（論理名）   |カラム名（物理名）        |型・桁                        |Nullable                      |その他コメント                 |
|:--------------------|:-------------------------|:-----------------------------|:----------------------------- |:----------------------------- |
| プロダクトコード    | product_code             | varchar(255)                 | No                            |   primary key                            |
| 機種名称            | model_name               | varchar(255)                 | No                            |                               |
### 出荷明細テーブル
|カラム名（論理名）   |カラム名（物理名）        |型・桁                        |Nullable                      |その他コメント                 |
|:--------------------|:-------------------------|:-----------------------------|:----------------------------- |:----------------------------- |
| 出荷指示書番号      | shipping_order_number    | varchar(255)                 | No                            |  foreign key                   |
| プロダクトコード    | product_code             | varchar(255)                 | No                            |   foreign key                            |
| 出荷数量            | shipment_quantity        | int                          | No                            |                               |
| 担当者              | person_in_charge         | varchar(255)                 | No                            | 担当者が未決定の時は"未割当"    |
| 進捗状況            | status                 | varchar(255)                 | No                            |                               |
| 作成日時            | created_at               | datetime                     | No                            | YYYY-MM-DD HH:MM:SS形式       |
| 更新日時            | updated_at               | datetime                     | No                            | YYYY-MM-DD HH:MM:SS形式       |

## URL設計
|機能   |メソッド                        | URL                             |
|:--------------------|:-------------------------|:--------------------------------|
| タスクを全件取得                 | GET                       | /tasks/                         |
| 指定されたパラメータのタスクを取得              | GET                       | /tasks/search                  |
| 指定された担当者のタスクを取得"                | GET                       | ​/person_tasks​/{person_in_charge}             |
| タスクを登録                 | POST                       | /tasks/                         |
| タスクを修正                 | PATCH                       | /tasks/{id}                     |
| タスクを削除                 | DELETE                       | /tasks/{id}                     |

