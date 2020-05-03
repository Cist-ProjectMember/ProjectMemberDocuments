# データベースとは？
データベース(Database,DB)とは、複数のアプリケーションやユーザーによってデータが共有できるように整理された、データの集合体のこと。<br> DBには「階層型DB」「ネットワーク型DB」など、いくつか種類があるが、現在では「リレーショナルDB」が主流となっている。また、データベースを管理するシステムのことを、データベース管理システム(DBMS)という。<br>
DBMSの一種にRDBMS(リレーショナルDBMS)がある。これは、行と列によって構成された「表形式のテーブル」と呼ばれるデータの集合を、互いに関連付けて関係モデルを使ったデータベースのことである。<br>  
RDBMSでは、表の行（横）を「タプル(レコード)」、表の列（縦）を「カラム」、表のマスを「フィールド」、表を「テーブル」と呼ぶ。リレーションとはテーブル同士の関係を設定し、関連付けるものである。2つ以上のテーブルから関連性のあるものを結合して新しい表を作ったり、フィールドの値を更新すると、関連性のあるテーブルの値も自動的に更新したりできる。<br>  
<img width="500" alt="illust1" src="https://github.com/emm93892/ProjectMemberDocuments/blob/master/2020s/supplement/database/%E5%9B%B31.png">

# SQLとは？
SQL(Structured Query Language：構造化問合せ言語)とは、RDBMSを操作するための言語だ。データベース自体にはExcelのように検索機能や他のシートを参照したりする機能はない。データを利用するには都度プログラムが必要であり、そのプログラム言語こそがSQLである。<br>

## SQLの基本構文
SQLの軸となるのが「キーワード」だ。キーワードとは、SQLにあらかじめ用意された命令のための語句である。このキーワードに、テーブルの名前や列の名前といったデータなどを組み合わせたものを単位として、それらを複数組み合わせることでSQL文が完成する。 キーワードと列名等の組み合わせを「句」と呼ぶ。このSQL文の書き方にはいくつかルールが存在する。<br>
<img width="500" alt="illust2" src="https://github.com/emm93892/ProjectMemberDocuments/blob/master/2020s/supplement/database/%E5%9B%B32.png">
1.	語句の間は半角スペースで区切る。
    文法上はいくついれても問題ない。Tabで代用できる。全角スペースはエラーになる。<br>
2.	最後に「;」(セミコロン)を付ける。<br>
    SQL文はセミコロンで文の終わりを判定する。セミコロンを付けるまでは文に続きがあるとみなされ、改行を挟んでも続けることが出来る。<br>
3.	文字列は「’」(シングルクォート)で囲う。<br>
4. キーワードの大文字と小文字は区別されない。

## データ型
データベースに入れるデータにはC言語の変数のように、型が存在する。ここでは、その代表的なデータ型を紹介する。
<img width="300" alt="illust3" src="https://github.com/emm93892/ProjectMemberDocuments/blob/master/2020s/supplement/database/%E5%9B%B33.png"><br>
固定長とは、入るデータの長さが決まっているという意味だ。<br>
CHAR型とは固定長の文字列を扱うデータ型であり、例えば、CHAR(10)と書かれていたら、10バイトの文字を格納するという意味になる。
もし、格納する文字列が10バイトではなく8バイトの場合、文字列の右側に2バイト分の空白が追加され、10バイトになった後に格納される。<br>
CHAR型は社員番号や郵便番号といった格納するデータの桁数が決まっているものに対して使われる。<br>
可変長とは、中に入るデータの長さが決まっていないという意味だ。<br>

VARCHAR型とは可変長の文字列を扱うデータ型である。
VARCHAR型では、格納するデータの文字列が足りていなくても、右側に空白を追加するといった調整はない。VARCHAR(10)と書かれていたら、10バイトまでなら、8バイトでも3バイトでもよく、そのままで格納することが可能という意味になる。<br>
VARCHAR型は氏名や書籍名といった、格納するデータの桁数が変動するものに対して使われる。<br>

# キーワード
## CREATE 
CREATE文は、テーブルのみならず、さまざまなデータベース上のオブジェクトを作成するために使われる。カラムにはデータ型(リンク)と列制約(リンク)が存在する。列制約は省略することが出来る。
```
CREATE TABLE [テーブル名](
		[カラム名1] [データ型] [列制約],
		[カラム名2] [データ型] [列制約],
		…
	);
```
実際にユーザの情報を管理するaccountテーブルをSQLを用いて作成する場合の例を以下に示す。

```
# accountテーブル作成例
CREATE TABLE account(
     id varchar(16) PRIMARY KEY,
     first_name varchar(32),
     last_name varchar(32)
     weight varchar(4),
     height varchar(4)
     rank varchar(16)
 );
```

上記のSQLのうち、idやfirst_name,last_nameは キー と呼ばれ、テーブルの列となる。
さらにその後ろにはデータ型を記述する。
varcharは文字列型(可変長)であり、()で指定した文字数分の記憶領域を持つ。

## INSERT 
テーブルに新しくレコードを追加するにはINSERT文を用いる。
```
INSERT INTO [テーブル名]([列1,列2, …])
VALUES ([列1に入れる値,列2に入れる値, …]);
```
以下にid、first_name、last_name、weight、height、rankカラムを持つaccountテーブルにデータを追加する場合の例を示す。
```
# accountテーブルにデータを追加する
INSERT INTO account(id,first_name,last_name,weight,height,rank)
 		VALUES(1, 'tanjiro', 'kamado',61,165,'hei');
```
このSQLを実行するとidが1、first_nameが"hikari"、last_nameが"chitose"、weightが61、heightが165、rankがheiのタプルがaccountテーブルに追加される。文字列をデータとする場合は、「’」(シングルクォート)で囲う。<br>
<br>
さらに、一つのINSERT文で複数のタプルを追加することも出来る。
```
# accountテーブルに一括でデータを追加する
INSERT INTO account(id,fist_name,last_name,weight,height,rank)
  			VALUES(2, 'nezuko', 'kamado’,45,153,null),
  			(3, 'shinobu', 'kotyo',37,151,'hashira'),
  			(4, 'giyu', 'tomioka',69,176,'hashira');
```

## SELECT
テーブルからデータを抽出する時には、SELECT文を用いる。
```
	SELECT [カラム名]
	FROM [テーブル名];
```
SELECT文を実行すると、実行結果がExcelのようなマトリックス表で表示される。<br>
カラム名に\[*](アスタリスク)を使用すると、全てのカラムが表示される。
```
	#accountテーブルからデータを表示する
		SELECT *
		FROM account;
```
SELECT文から派生して、複数のテーブルを結合、列と列を結合演算子を使用して計算列の値をExcelの関数と同じように使用(例えば、何桁目から何桁目の文字を取得など)、どのような条件でデータを絞りこむのか、どの順番にデータを並べるか、が可能となる。<br>

### ORDER BY
テーブルからSELECTでデータを取得する時、ORDER BY句を使うと、指定された列を基準に並べ替えることができる。
```
	SELECT *
	FROM account
	ORDER BY height;
```
ORDER BY 〇〇 ASC/DESCを書くこともでき、ASCが昇順、DESCが降順となる。
省略した場合は昇順となる。

## 演習1
#### 1.表1のテーブル構造情報を基に、student_grade_informationを作成し、表2のデータを入れなさい。その後、テーブルのデータを表示しなさい。<br>

***表1 テーブル構造情報***
| カラム名 | データ種別 |
----------|------------
| id | integer |
| student_name | varchar(8) |
| math_score | integer |
| english_score | integer |

***表2 入力情報***
| id | student_name | math | english |
-----|--------------|------|--------
| 1 | A | 60 | 60 |
| 2 | B | 80 | 80 |
| 3 | C | 0 | 0 |

####  2.mathを基準に降順でソートしなさい。
