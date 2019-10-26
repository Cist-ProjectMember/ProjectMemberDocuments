# データベース応用-1

## キーワード

## 概要

[H2DBのデータ型](https://www.h2database.com/html/datatypes.html)
[H2DBの集約関数](https://www.h2database.com/html/functions-aggregate.html)

## 演習課題

### 取り組む前に

春学期に引き続きH2DBを用いるため、自前のPCで課題に取り組む場合は事前に環境構築をしておくこと。</br>
IntelliJを使用する場合は専用のウィンドウからデータベースの操作ができるが、この課題では直接SQLを書き込んで実行すること。</br>

### 課題1

SQLを発行して以下のカラムを持つaccountテーブルを作成しなさい。

|カラム名|データ型|列制約|  
|---|---|---|
|id|bigint|主キー|
|name|varchar(64)|非NULL|
|password|varchar(32)|非NULL|

### 課題2

SQLを発行してaccountテーブルに以下のデータを追加しなさい。

|id|name|password|
|---|---|---|
|1|account1|account1spass|
|2|account2|account2spass|
|3|account3|account3spass|
|4|account4|account4spass|

### 課題3

count関数を使用してaccountテーブルの行数を取得しなさい。

### 課題4


