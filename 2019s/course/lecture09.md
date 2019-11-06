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


### 課題2
