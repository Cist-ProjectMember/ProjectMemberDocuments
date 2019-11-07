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
第8回で作成したテーブルに以下のデータを追加してください。

ここからデータをinsertしていきます。以下のデータをinsertしてください。

データ一覧  

|name|student_number|department|  
|---|---|---|  
|sachiko|b2180001|電子光工学科|
|yuta|b2180002|情報システム工学科|
|ren|b2180003|応用化学生物学科|
|hayato|b2180004|応用化学生物学科|
|mizuki|b2180005|電子光工学科|
|sakura|b2180006|情報システム工学科|

### 課題2
課題1のデータを全て表示してください。また、`情報システム工学科`の人だけを表示できるようにしてください。

### 課題3
課題1で作成したデータに間違いがあった。以下のデータを書き換えて（更新して）ください。  

1. `ren`の学籍番号を`b2180003`から`b2180007`に変更してください。  
2. `mizuki`のの学籍番号を`b2180005`から`b2170005`に変更してください。


### 課題4
先ほど以下の学生が退学しました。その人のデータを削除してください。  

|name|student_number|department|
|---|---|---|
|sachiko|b2180001|電子光工学科|
|hayato|b2180004|応用化学生物学科|


### 課題5

学生のデータのうち、名前を辞書順でソートしてください。  





