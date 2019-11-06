# データベース基礎-1

## キーワード

* データベース
* SQL
* テーブル
* カラム
* タプル(レコード)
* CREATE
* INSERT
* SELECT

## 概要

### データベースとは

特定のルールに従い、データを蓄積&整理して使いやすくしたものである。</be>
大まかに言うと、MSOfficeのExcelや、スプレッドシートのような、表(のような)形式でデータを管理することができるものである。</br>
例えば、以下のようなデータはデータベースで管理されることが多い。

* ログインに必要なアカウント情報
  * ID
  * パスワード
* 個人情報
  * 氏名
  * 年齢
  * 住所
  * 電話番号
  * メールアドレス
  * 勤めている企業
* 企業
  * 企業コード
  * 社名
  * 業種

これらはデータベースで管理されるデータのほんの一部であり、世の中には数え切れないほどのデータ、データベースが存在する。

また、データベースを管理するシステムのことを、データベース管理システム(DBMS)という。

### RDBMSとSQL

プログラミング言語に種類があるように、DBMSにも種類がある。</br>
DBMSの一種であるRDBMS(リレーショナルDBMS)は、表のような形式で表現され、テーブルや属性、キーなどによって構成されている。</br>
RDBMSに対してクエリ(問い合わせ)を行うことでデータの取得や更新、削除などが出来るようになる。</br>
問い合わせをする場合にはDBMSが理解できる言語を用いる必要があるが、この問い合わせをする際に用いる言語がSQLである。

例えば、accountテーブルの全てのデータを取得するには以下のようなSQLを記述する。

```sql
# accountテーブルの全データを表示
SELECT * FROM account;
```

### SQL文法

#### CREATE

CREATE文を用いることで新しくテーブルを作成することができる。</br>
実際にはテーブルを作成する場合にはCREATEの後ろにTABLEをつける必要がある。

```sql
# テーブル作成例
CREATE TABLE [テーブル名](
  [カラム名1] [データ型] [列制約],
  [カラム名2] [データ型] [列制約],
  ...
);
```

実際にユーザの情報を管理するaccountテーブルをSQLを用いて作成する場合の例を以下に示す。

```sql
CREATE TABLE account(
  id varchar(16) PRIMARY KEY,
  first_name varchar(32),
  last_name varchar(32),
);
```

上記のSQLのうち、idやfirst_name,last_nameは *キー* と呼ばれ、テーブルの列となる。

さらにその後ろにはデータ型を記述する。</br>
varcharは文字列型(可変長)であり、()で指定した文字数分の記憶領域を持つ。

H2DBでどのようなデータ型を指定できるのかは、[H2DBのデータ型](http://www.h2database.com/html/datatypes.html)を参照のこと。

#### INSERT

テーブルに新しくレコードを追加するにはINSERT文を用いる。

```sql
INSERT INTO account(id,first_name,last_name)
 VALUES(1, 'hikari', 'chitose');
```

このSQLを実行するとidが1、first_nameが"hikari"、last_nameが"chitose"のレコードがaccountテーブルに追加される。

#### SELECT

テーブルのデータを検索(表示)するにはSELECT文を用いる。

```sql
SELECT * FROM account;
```

INSERTを実行後にこのSQLを実行すると、追加したデータがコンソール上に表示される。

### 用語

#### テーブル

列(カラム)と行(タプル、レコード)から構成される。

```text
+--+----------+---------+
|id|first_name|last_name|
+--+----------+---------+
|1 |hikari    |chitose  |
|2 |hanako    |yamada   |
+--+----------+---------+
```

#### カラム

テーブルにおける列のこと。

#### タプル

テーブルにおける行のこと。レコードと呼ばれることもある。

## 演習課題

### 課題1

新たにstudent_informationテーブルを作成し、以下のカラムを設定しなさい。

|カラム名|データ型|
|---|---|
|name|varchar(64)|
|student_number|varchar(16)|
|department|varchar(32)|

また、student_informationテーブルに下の指示に従い自分の情報を入れなさい。

|カラム名|内容|
|---|---|
|name|あなたの名前(ローマ字表記の姓名を半角スペース区切りで)|
|student_number|あなたの学籍番号(bxxxxxx0)|
|department|あなたの所属学科|

### 課題2

SQLを発行し、student_informationテーブルのデータを表示しなさい。
