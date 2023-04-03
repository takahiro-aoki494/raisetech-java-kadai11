# 最終課題概要
タスクの一覧を管理するAPIを作成予定
<br>仕様書は下記です。</br>
https://github.com/takahiro-aoki494/raisetech-java-kadai11/swagger

## データベース定義
|カラム名（論理名）   |カラム名（物理名）        |型・桁                        |Nullableb                      |その他コメント                 |
|:--------------------|:-------------------------|:-----------------------------|:----------------------------- |:----------------------------- |
| ID                  | id                       | long                         | No                            | primary key                   |
| 出荷指示書番号      | shipping_order_number    | varchar(255)                 | No                            |                               |
| 納入予定日          | delivery date            | date                         | No                            | YYYY-MM-DD形式                |
| 出荷予定日          | estimated_shipping_date  | date                         | No                            | YYYY-MM-DD形式                |
| 検査完了予定日      | inspection_complete_date | date                         | No                            | YYYY-MM-DD形式                |
| 担当者              | person_in_charge         | varchar(255)                 | No                            | 担当者が未決定の時は"未割当"    |
| 進捗状況            | progress                 | varchar(255)                 | No                            |                               |
| 出荷数量            | shipment_quantity        | int                          | No                            |                               |
| プロダクトコード    | product code             | varchar(255)                 | No                            |                               |
| 機種名称            | model_name               | varchar(255)                 | No                            |                               |
| 作成日時            | created_at               | datetime                     | No                            | YYYY-MM-DD HH:MM:SS形式       |
| 更新日時            | updated_at               | datetime                     | No                            | YYYY-MM-DD HH:MM:SS形式       |


## URL設計
|機能   |メソッド                        | URL                             |
|:--------------------|:-------------------------|:--------------------------------|
| タスクを全件取得                 | GET                       | /tasks/                         |
| タスクを1件取得                 | GET                       | /tasks/{id}                     |
| タスクを登録                 | POST                       | /tasks/                         |
| タスクを修正                 | PATCH                       | /tasks/{id}                     |
| タスクを削除                 | DELETE                       | /tasks/{id}                     |


