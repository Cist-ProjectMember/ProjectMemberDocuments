# データベースとは？
データベース(Database,DB)とは、複数のアプリケーションやユーザーによってデータが共有できるように整理された、データの集合体のこと。<br> DBには「階層型DB」「ネットワーク型DB」など、いくつか種類があるが、現在では「リレーショナルDB」が主流となっている。また、データベースを管理するシステムのことを、データベース管理システム(DBMS)という。<br>
DBMSの一種にRDBMS(リレーショナルDBMS)がある。これは、行と列によって構成された「表形式のテーブル」と呼ばれるデータの集合を、互いに関連付けて関係モデルを使ったデータベースのことである。<br>  
RDBMSでは、表の行（横）を「タプル(レコード)」、表の列（縦）を「カラム」、表のマスを「フィールド」、表を「テーブル」と呼ぶ。リレーションとはテーブル同士の関係を設定し、関連付けるものである。2つ以上のテーブルから関連性のあるものを結合して新しい表を作ったり、フィールドの値を更新すると、関連性のあるテーブルの値も自動的に更新したりできる。<br>  
<img width="500" alt="illust1" src="https://github.com/emm93892/ProjectMemberDocuments/blob/master/2020s/supplement/database/%E5%9B%B31.png">

# SQLとは？
SQL(Structured Query Language：構造化問合せ言語)とは、RDBMSを操作するための言語だ。<br>データベース自体にはExcelのように検索機能や他のシートを参照したりする機能はない。<br>データを利用するには都度プログラムが必要であり、そのプログラム言語こそがSQLである。<br>

## SQLの基本構文
SQLの軸となるのが「キーワード」だ。キーワードとは、SQLにあらかじめ用意された命令のための語句である。<br>このキーワードに、テーブルの名前や列の名前といったデータなどを組み合わせたものを単位として、それらを複数組み合わせることでSQL文が完成する。<br> キーワードと列名等の組み合わせを「句」と呼ぶ。このSQL文の書き方にはいくつかルールが存在する。<br>
<img width="500" alt="illust2" src="https://github.com/emm93892/ProjectMemberDocuments/blob/master/2020s/supplement/database/%E5%9B%B32.png">
1.	語句の間は半角スペースで区切る。<br>
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
```sql
CREATE TABLE [テーブル名](
		[カラム名1] [データ型] [列制約],
		[カラム名2] [データ型] [列制約],
		…
	);
```
実際にユーザの情報を管理するaccountテーブルをSQLを用いて作成する場合の例を以下に示す。

```sql
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

上記のSQLのうち、idやfirst_name,last_nameは キー と呼ばれ、テーブルの列となる。<br>
さらにその後ろにはデータ型を記述する。<br>
varcharは文字列型(可変長)であり、()で指定した文字数分の記憶領域を持つ。

## INSERT 
テーブルに新しくレコードを追加するにはINSERT文を用いる。
```sql
INSERT INTO [テーブル名]([列1,列2, …])
VALUES ([列1に入れる値,列2に入れる値, …]);
```
以下にid、first_name、last_name、weight、height、rankカラムを持つaccountテーブルにデータを追加する場合の例を示す。
```sql
# accountテーブルにデータを追加する
INSERT INTO account(id,first_name,last_name,weight,height,rank)
 		VALUES(1, 'tanjiro', 'kamado',61,165,'hei');
```
このSQLを実行するとidが1、first_nameが"hikari"、last_nameが"chitose"、weightが61、heightが165、rankがheiのタプルがaccountテーブルに追加される。文字列をデータとする場合は、「’」(シングルクォート)で囲う。<br>
<br>
さらに、一つのINSERT文で複数のタプルを追加することも出来る。
```sql
# accountテーブルに一括でデータを追加する
INSERT INTO account(id,fist_name,last_name,weight,height,rank)
  			VALUES(2, 'nezuko', 'kamado’,45,153,null),
  			(3, 'shinobu', 'kotyo',37,151,'hashira'),
  			(4, 'giyu', 'tomioka',69,176,'hashira');
```

## SELECT
テーブルからデータを抽出する時には、SELECT文を用いる。
```sql
SELECT [カラム名]
FROM [テーブル名];
```
SELECT文を実行すると、実行結果がExcelのようなマトリックス表で表示される。<br>
カラム名に\[*](アスタリスク)を使用すると、全てのカラムが表示される。
```sql
#accountテーブルからデータを表示する
SELECT *
FROM account;
```
SELECT文から派生して、複数のテーブルを結合、列と列を結合演算子を使用して計算列の値をExcelの関数と同じように使用(例えば、何桁目から何桁目の文字を取得など)、どのような条件でデータを絞りこむのか、どの順番にデータを並べるか、が可能となる。<br>

### ORDER BY
テーブルからSELECTでデータを取得する時、ORDER BY句を使うと、指定された列を基準に並べ替えることができる。
```sql
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


## WHERE
SELECT文や後述するUPDATE文やDELETE文で、条件を指定する時に用いる。
```sql
#SELECT文での例
SELECT [カラム名]
FROM [テーブル名];
WHERE (条件);
```
条件には、=、>、<、!=、などの基本的な比較演算子の他に、論理演算子が使用できる。
<img width="500" alt="illust4" src="https://github.com/emm93892/ProjectMemberDocuments/blob/master/2020s/supplement/database/%E5%9B%B37.png"><br>

### BETWEEN
BETWEEN演算子はSQLで唯一の三項演算子である。これは、ある値(上の表ではＡ)が特定の範囲(B<=A<=C)であるかどうかを判定する時に用いられる。
表の式は、A>=B AND A>= C と同値である。
```sql
#accountテーブルのheightが150から160の値のタプルのデータを表示する
SELECT *
FROM account
WHERE height BETWEEN 150 AND 160;
```

### NOT
NOT演算子では、与えられた条件以外を指定する。
「～以外の」という条件を使いたい場合、NOTを使用すると効率的である。
```sql
#accountテーブルのlast_nameが’kamado’以外の値のタプルのデータを表示する	
SELECT *
FROM account
WHERE NOT last_name = ‘kamado’;
```

### IS NULL
IS NULL演算子は、値がNULLかどうかを判定し、boolean型で値を返す演算子である。
比較演算子は、NULLが存在する場合、NULLを返すと定められているので値を得ることはできない。
```sql
#accountテーブルのrankがNULLのタプルのデータを表示する
SELECT *
FROM account
WHERE rank IS NULL;
```
逆に、IS NOT NULLと指定すれば、NULLではない値のデータを表示することが出来る。

## UPDATE
タプルの値を更新する時は、UPDATE文を用いる。
```sql
UPDATE [テーブル名]
SET [列名1] = “値1” , [列名2] =”値2”
WHERE (条件);
```
SET句には更新する列名と値を記述する。
Where句の条件に一致した行を更新する。Where句が無い場合、全てのタプルを更新する。
```sql
#accountテーブルのデータを更新する
UPDATE account
SET first_name = “inosuke” , last_name =”hashibira”
WHERE id = 1;
```

## DELETE
タプルの値を削除する時には、DELETE文を用いる。
```sql
DELETE FROM [テーブル名]
WHERE (条件);
```
UPDATE文と同様に、WHERE句が無い場合は全てのタプルを削除する。
DELETE文では、WHERE句の条件に合致するタプル全てが削除される。
```sql
#accountテーブルの値を削除する
DELETE FROM account
WHERE id = 2;
```

## DROP
テーブルを削除するときに、DROP文を用いる。
```sql
DROP TABLE [テーブル名];
```
```sql
#accountテーブルを削除する
DROP TABLE account;
```


## 演習2
#### 1.表3のテーブル構造情報をもとにsales_historyを作成し、表4の情報を入れなさい。その後、テーブルのデータを表示しなさい。

***表3 データ構造***
|カラム名|データ種別|
---|---
|id|integer|
|product_name|varchar(16)|
|price|integer|
|date|date|

***表4　入力情報***
|id|product_name|price|data|
---|---|---|---
|1|マスク|500|2020-04-01|
|2|マスク|500|2020-04-01|
|3|トイレットペーパー|200|2020-04-02|
|4|トイレットペーパー|200|2020-04-02|
|5|消毒液|300|2020-04-03|
|6|消毒液|300|2020-04-03|
|7|マスク|500|2020-04-04|
|8|空気除菌剤|5000|2020-04-04|
|9|タンポポ茶|10000|2020-04-05|
|10|タンポポ茶|10000|2020-04-05|

#### 2.マスクが売れた日の日付を表示しなさい。
#### 3.2020-04-04から2020-04-05のデータをすべて表示しなさい。
#### 4.空気除菌剤のpriceを100に更新しなさい。
#### 5.タンポポ茶を販売したデータをすべて削除しなさい。


## 列制約
SQLの表定義ではデータ値に制約を持たせることで、登録されるデータが常に正しい状態を保つことができる。<br>制約には「列制約」と「テーブル制約」という 2つの基本制約がある。両者の違いは、列制約が列のみに適用されるのに対し、テーブル制約が列のグループに適用されるということである。
<img width="500" alt="illust5" src="https://github.com/emm93892/ProjectMemberDocuments/blob/master/2020s/supplement/database/%E5%9B%B34.png"><br>

### PRIMARY KEY
主キーとも呼ばれる。テーブルの各行(タプル)を一意に識別するための 1つ以上の列(カラム)のグループのことである。一つのテーブルに一つ存在することが出来る。
### UNIQUE KEY
一意性制約とも呼ばれる。列にUNIQUE列制約を設定すると、既に他の行に存在する値の設定を拒否することができる。ただし、NULLの重複は可能である。
### CHECK
この制約を利用することで、テーブルに入力されるデータを受理するにあたって、満たさなければならない条件を定義できる。
### DEFAULT
テーブルへのINSERT文に列の値が指定されなかった時に、そのテーブルの値に自動的に挿入される値を決めることができる。
### NOT NULL
この制約が設定された列へのINSERT文に値が指定されなかった時に、エラーを返す。
### FOREIGN KEY
テーブル間でデータの整合性を保つために、関連付けを行う参照整合性制約がある。<br>
親テーブルに従属する子テーブルに定義されている参照列を外部キー(FOREIGN KEY)という。<br>
主キーを PK と省略して言うように、よく外部キーのことを FK とも言われる。<br>

子テーブルの関連データに対するオプションとして、on delete cascade や on delete set null がある。
オプションの使い方を間違えると消失リスクもある。

#### ON DELETE CASCADE
親テーブルの行が削除される場合、参照している子テーブルの該当行も削除される。
```sql
FOREIGN KEY [子テーブルのカラム名] REFERENCES [親テーブルのテーブル名] [親テーブルのカラム名] ON DELETE CASCADE
```
#### ON DELETE SET NULL
親テーブルの行が削除される場合、参照している子テーブルの該当行は null に更新される。
```sql
FOREIGN KEY [子テーブルのカラム名] REFERENCES [親テーブルのテーブル名] [親テーブルのカラム名] ON DELETE SET NULL 
```
## 内部結合
内部結合とは、2つのテーブルでそれぞれ結合の対象となるカラムを指定し、それぞれのカラムに同じ値が格納されているデータを結合して取得するものである。
次の図を見てほしい。<br>
<img width="600" alt="illust6" src="https://github.com/emm93892/ProjectMemberDocuments/blob/master/2020s/supplement/database/%E5%9B%B38.png">

userテーブルとfacultyテーブルを内部結合する。結合の対象となるカラムは、userテーブルの「faculty_ID」と、facultyテーブルの「ID」だ。この2つのカラムの値が同じデータ同士を結合し取得する。<br>
SELECT 文と INNER JOIN 句を組み合わせることで2つのテーブルを内部結合させてデータを取得することができる。
```sql
SELECT [取得するカラム] FROM [テーブル名1]
INNER JOIN [テーブル名2] ON (条件);
```
取得するカラムは、どちらのテーブルにあるどのカラムなのかが分かるように「テーブル名.カラム名」の形式で指定する。条件のところでは結合の対象となるカラムについて「テーブル名1.カラム名1 = テーブル名2.カラム名2」の形式で指定する。<br>

上の表を用いた例文が以下の通りだ。<br>
```sql
SELECT * FROM user
INNER JOIN faculty ON user.faculty_ID = faculty.ID;
```
このとき、取得したデータにはIDカラムが2つ含まれている。このように複数のテーブルに同じ名前のカラムがある場合にこのカラムをを指定して取得したい場合には次のように「テーブル名.カラム名」の形で指定する。<br>
どちらかのテーブルにしか含まれておらずテーブル名を省略してもどちらのテーブルのカラムか分かる場合には「テーブル名.」の部分を省略して「カラム名」だけでも可能だ。今回は、userテーブルの「faculty_ID」がそれに当たる。<br>
```sql
SELECT user.id , user.name , faculty_ID , faculty.name FROM user
INNER JOIN faculty ON user.faculty_ID = faculty.ID;
```
上のコードの実行結果が以下の通りだ。 <br>
<img width="500" alt="illust7" src="https://github.com/emm93892/ProjectMemberDocuments/blob/master/2020s/supplement/database/%E5%9B%B39.png">


## 演習3
#### 1.表5のテーブル構造情報をもとにstudent_informationを作成し、表6の情報を入れなさい。その後、テーブルのデータを表示しなさい。

***表5　テーブル構造***
|カラム名|データ型|列制約|備考|
--|--|--|--
|student_number|integer|主キー|   |
|name|varchar(8)|非NULL|   |

***表6　入力情報***
|student_number|name|
--|--
|1|a|
|2|b|
|3|c|
|4|d|
|5|e|

#### 2.表7のテーブル構造情報をもとにchoice_electivesを作成し、表8の情報を入れなさい。なお、student_informationのstudent_numberを親カラムとし、choice_electivesのstudent_numberを子カラムとしたforeign key制約も設定しなさい。参照制約動作は親カラムが更新、削除されたら追従する。

***表7 テーブル構造***
|カラム名|データ型|列制約|備考|
--|--|--|--
|student_number|integer|主キー|親テーブル=stundet_infromation、親カラム=student_number、子テーブル=chioce_electives、子カラム=student_number、親カラムが更新、削除されたら子カラムも追従させる。|
|electives_1|varchar(8)|非NULL|   |
|electives_2|varchar(8)|非NULL|   |

***表8　入力情報***
|student_number|electives_1|electives_2|
--|--|--
|1|数学|英語|
|2|英語|数学|
|3|英語|数学|
|4|物理|化学|
|5|生物|化学|

#### 3.electives_1が英語のデータを表示しなさい。なお、student_information(student_number,name)、choice_electives(electives_1,electives_2)を表示させること。
#### 4.student_informationからidが5のタプルを削除しなさい。その後、choice_electivesから、idが5のタプルが消えていることを確認しなさい。
