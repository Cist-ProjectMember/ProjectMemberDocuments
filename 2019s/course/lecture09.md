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
もし、第8回で所属学科を漢字にした場合は漢字にすること。

データ一覧  

|名前|学籍番号|所属学科|  
|---|---|---|  
|SachikoKobayashi|b2180001|denshi|
|YutaYamamoto|b2180002|joho|
|RenSato|b2180003|ouyou|
|HayatoSuzuki|b2180004|ouyou|
|MizukiTakahashi|b2180005|denshi|
|SakuraNakamura|b2180006|joho|

### 課題2
課題1のデータを全て表示してください。また、`Joho`の人だけを表示できるようにしてください。

### 課題3
課題1で作成したデータに間違いがあった。以下のデータを書き換えて（更新して）ください。  

1. `RenSato`の学籍番号を`b2180003`から`b2180007`に変更してください。  
2. `MizukiTakahashi`のの学籍番号を`b2180005`から`b2170005`に変更してください。


### 課題4
先ほど以下の学生が退学しました。その人のデータを削除してください。  

|名前|学籍番号|所属学科|
|---|---|---|
|SachikoKobayashi|b2180001|denshi|
|HayatoSuzuki|b2180004|ouyou|


### 課題5

学生のデータのうち、名前を辞書順でソートしてください。  





