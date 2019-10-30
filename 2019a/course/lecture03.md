# データベース応用-1

## キーワード

* H2DB
* NOT NULL
* UNIQUE
* PRIMARY KEY
* FOREIGN KEY

## 概要

2019年度後期プロジェクトメンバーの講習では、前期に引き続き[H2DB](https://www.h2database.com/html/main.html)をDBMSとして使用する。</br>
前期プロジェクトメンバーのDB編の講習終了時点程度の知識を持っていることを前提とした資料のため、事前に必要な知識を揃えておくこと。</br>

H2DB(に限らずその他の大半のデータベースも)には、テーブルのカラムに特定の制限を付ける "列制約" というものが存在する。</br>
列制約は以下に挙げるように多くの種類があり、それぞれを組み合わせて使用することも出来る。</br>

### 列制約

#### NOT NULL制約

NOT NULL制約が付与されたカラムは空欄にすることができない。

```sql
create table example(
  name varchar(32) NOT NULL,
);
```

#### UNIQUE制約

UNIQUE制約が付与されたカラムは一意でなければならない(同じデータが入ることを禁止する)。

```sql
create table example(
  id varchar(16) UNIQUE,
  password varchar(32) NOT NULL,
);
```

#### PRIMARY KEY制約

PRIMARY KEY制約が付与されたカラムは主キーであることを意味する。</br>
H2DBではPRIMARY KEYを指定すると、そのカラムにはNOT NULLとUNIQUEが付与される。

```sql
create table example(
  id varchar(16) PRIMARY KEY,
  age integer NOT NULL,
  amount bigint NOT NULL,
);
```

#### FOREIGN KEY制約

FOREIGN KEY制約が付与されたカラムは他のテーブルのカラムを参照するようになる。</br>
参照先が変更されると参照元のデータも同時に変更されるようになる(削除も同様)。</br>
参照先が変更された場合にどのような処理がされるかを指定することも出来る。</br>
さらに、外部キーの参照先に無いレコードを追加しようとするとエラーが発生するようになる(参照整合性制約違反)。</br>

以下に、FOREIGN KEY制約を使用する場合の例を示す。</br>
FOREIGN KEYの引数部分に、外部キーにしたいキー(参照元)を指定する。</br>
REFERENCESにはどのテーブルのどのキーを参照させるか(参照先)を指定する。

```sql
CREATE TABLE example(
  another_table_id INTEGER PRIMARY KEY,
  some_key INTEGER NOT NULL,
  FOREIGN KEY (another_table_id)
  REFERENCES another_table(id)
);
```

また、参照先や参照元の値が変更された/削除されたときの動作も定義することができる。

##### CASCADE

FOREIGN KEYを定義する際に、参照先の値が変更された場合に参照元の値も変更させたい場合には以下のように記述する。

```sql
CREATE TABLE example(
  another_table_id INTEGER PRIMARY KEY,
  some_key INTEGER NOT NULL,
  FOREIGN KEY (another_table_id)
    REFERENCES another_table(id)
      ON UPDATE CASCADE,
);
```

この例では、another_tableのidが更新された場合に、参照元(この場合はexampleテーブルのanother_table_id)の値も連動して更新される。

```sql
CREATE TABLE example(
  another_table_id INTEGER PRIMARY KEY,
  some_key INTEGER NOT NULL,
  FOREIGN KEY (another_table_id)
    REFERENCES another_table(id)
      ON DELETE CASCADE,
);
```

この例では、another_tableのレコードが削除された場合に、参照元(この場合はexampleテーブルのanother_table_id)の対応するレコードも連動して削除される。

また、更新時/削除時の挙動はどちらも同時に定義することができる。

## 演習課題

### 取り組む前に

春学期に引き続きH2DBを用いるため、自前のPCで課題に取り組む場合は事前に環境構築をしておくこと。</br>
IntelliJを使用する場合は専用のウィンドウからデータベースの操作ができるが、この課題では直接SQLを書き込んで実行すること。</br>

### 課題1

SQLを発行して以下のカラムを持つaccountテーブルを作成しなさい。

|カラム名|データ型|列制約|備考|
|---|---|---|---|
|id|bigint|主キー|-|
|name|varchar(64)|非NULL|-|
|password|varchar(32)|非NULL|-|

### 課題2

SQLを発行してaccountテーブルに以下のデータを追加しなさい。</br>
また、accountテーブルのデータを全て表示しなさい。

|id|name|password|
|---|---|---|
|1|account1|account1pass|
|2|account2|account2pass|
|3|account3|account3pass|
|4|account4|account4pass|

### 課題3

SQLを発行して以下のカラムを持つgradeテーブルを作成しなさい。

|カラム名|データ型|列制約|備考|
|---|---|---|---|
|account_id|bigint|主キー|accountテーブルのidを参照する|
|grade|integer|非NULL|-|

### 課題4

SQLを発行してgradeテーブルに以下のデータを追加しなさい。</br>

|account_id|grade|
|---|---|
|1|1|
|2|1|
|3|3|
|4|2|

### 課題5

gradeが2以上のデータを表示しなさい。
ただし、account(id,name)とgrade(grade)を表示すること。

**表示例**

```text
+--+--------+-----+
|id|name    |grade|
+--+--------+-----+
|3 |account3|3    |
|4 |account4|2    |
+--+--------+-----+
```

### 課題6

SQLを発行してgradeテーブルに以下のデータを追加しなさい。</br>
また、追加できなかった場合はその理由を考えなさい。

|account_id|grade|
|---|---|
|5|1|
|6|3|

### 課題7

SQLを発行してaccountテーブルからidが1のレコードを削除しなさい。</br>
また、SQLを発行してgradeテーブルからaccount_idが1のレコードが削除されていることを確認しなさい。

