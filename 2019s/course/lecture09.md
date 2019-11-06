# データベース基礎-2

## キーワード

* UPDATE
* DELETE
* SELECT
* WHERE
* ORDER BY
* ASC
* DESC

## 概要

### レコードの検索

レコードの検索をするにはSELECT文を用いる。</br>

```sql
SELECT [表示したい列名1](, [表示したい列名2], ...) FROM [テーブル名];
```

以下にaccountテーブルからすべてのデータを検索(表示)する場合の例を示す。

```sql
SELECT * FROM account;
```

#### フィルタ

```sql
SELECT * FROM account WHERE id = 1;
```

### レコードの更新

```sql
UPDATE account SET name = 'changed' WHERE id = 1;
```

```sql
UPDATE account SET grade = 2 WHERE grade = 1;
```

### レコードの削除

```sql
DELETE FROM account WHERE id = 1;
```

#### ソート

```sql
# idで降順に表示
SELECT * FROM account ORDER BY id DESC;
```

```sql
# idで昇順に表示
SELECT * FROM account ORDER BY id ASC;
```

## 演習課題

### 課題1
lectureに新たにstudent_informationというテーブルを作成します。データは以下を参考にしてください。


|カラム名|データ型|
|---|---|
|name|varchar(64)|
|student_number|varchar(16)|
|department|varchar(32)|

ここからデータをinsertしていきます。以下のデータをinsertしてください。
- 文字は小文字にすること
- それぞれの名前の英語については各自で考えて命名してください（あまりわけわからないものにはしないように）

データ一覧
|名前|学籍番号|所属学科|  
|---|---|---|  
|コバヤシサチコ|b2180001|電子光工学科|
|ヤマモトユウタ|b2180002|情報システム工学科|
|サトウレン|b2180003|応用化学生物学科|
|スズキハヤト|b2180004|応用化学生物学科|
|タカハシミズキ|b2180005|電子光工学科|
|ナカムラサクラ|b2180006|情報システム工学科|

### 課題2
課題1で作成したデータに間違いがあった。以下のデータを書き換えて（更新して）ください。  
ヒント
