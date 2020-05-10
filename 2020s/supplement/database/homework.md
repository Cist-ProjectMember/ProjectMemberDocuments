# データベース課題

　演習でSQLの書き方を学んだと思うので宿題ではその前段階のデータ型や列制約を決めることを行いたいと思います。  
これから成果物を作るにあたって、データベースを使用する学生は多いと思います。今のうちに軽く練習しましょう。

## 課題

　次の図を見て、2つのテーブルを作成せよ。
ただし、データ型及び列制約は自分で考察すること。  
また、各名称を英語で記載すること。H2のデータ型は[ここ](http://www.h2database.com/html/datatypes.html)を参照せよ。  
<br>
<img width="500" alt="illust1" src="https://github.com/Cist-ProjectMember/ProjectMemberDocuments/blob/master/2020s/supplement/database/image/%E5%9B%B310%20(2).png">

図1．販売管理システムのE-R図

## 解答

　データベースはどれが正しいなどは決めづらいのであくまで例として参考にしてください。  
英語については僕も得意ではないので、間違っているところがあればチームの3年生に教えてください。  
```sql
# 解答例
# 顧客テーブル
CREATE TABLE CUSTOMER(
     ID                       CHAR(5)        PRIMARY KEY,
     NAME                     VARCHAR(60),
     ACCOUNT_REPRESENTATIVE   VARCHAR(60),
     ACCOUNT_EXECUTIVE        VARCHAR(60),
     ADDRESS                  VARCHAR(483)
 );
# 請求テーブル
CREATE TABLE BILL(
     ID                  CHAR(5)   PRIMARY KEY,
     CUST_ID             CHAR(5),
     DATE                DATE,
     APPROPRIATE_DATE    DATE,
     AMOUNT              NUMERIC,
     PURCHASE_AMOUNT     NUMERIC,
     CLEAR_AMOUNT        NUMERIC,
     FOREIGN KEY (CUST_ID) REFERENCES CLIENT (CUST_ID)
);
```

## 解説 

### データ型

　データ型は宗教問題になりかねになりかねないので、あくまで例として確認ください。  
講習会でも説明した通り、データ型は大きく分けて以下のように区別することができます。 
<br>
<img width="500" alt="illust1" src="https://github.com/Cist-ProjectMember/ProjectMemberDocuments/blob/master/2020s/supplement/database/image/%E5%9B%B33.png">

今回の課題はカラムを番号関連、日付関連、金額関連、テキスト関連で分けられます。  
それぞれについて解説していきます。

#### 番号

　番号は学籍番号のように「b21○○○○○」のように数字以外の文字を使うことがよくあります。  
今回は指定がなかったため、おそらく"INTEGER"などを使用した学生もいるかと思います。  
どちらが正しいなどはないですが、"CHAR"を使うことがあることも覚えておきましょう。  
また、charではなくvarcharを使った方がいいという意見もあります。

#### 日付

　日付や時刻には"DATETIME", "DATE", "TIME"、"TIMESTAMP"など数多くの方が存在します。  
最初のころは、時刻は"TIME"・日付は"DATE"・日時は"DATETIME"と覚えていただいていいと思います。  
今回は「請求日」と「計上年月」の2点でどちらも日付なので"DATE"が適切だと思います。  

#### 金額

　金額は"NUMERIC"もしくは"MONEY"を用いることが多いです。  
"INTEGER"とは数値の正確さに違いがあり、金額のような正確さが求められるものには"INTEGER"などはあまり適していません。  
ただ必ずしも間違っているわけではないです。（データベース本当に難しい・・・）  
　サイズについてはこの問題文からは決められないので各自適当に。  

#### テキスト

　テキストはこの場合「顧客名」「顧客担当者名」「営業担当者名」「住所」のことを指します。  
これらで用いる主な型は"varcher","text","name"です。どれが一番かは僕もわかりません()。  
　
 ここではサイズ（型のあとに書く数字）について話します。  
基本サイズは実際よりも多めに見積もります。  
今回は[このサイト](https://kyogom.com/tech/design/maxlength/)を基にバイト数を作成しました。  

### 列制約

　今回の問題では、主キー(PRIMARY KEY)と外部キー(FOREIGN KEY)を用います。  
この2つはどんなデータベースを作る場合でも必須になるほど重要なものですので、  
すぐに見極められるようになりましょう。  

　この二つの制約を使う際に注意してほしい点はどちらに矢印が向いているかです。  
2つのテーブルを作る際には、矢印が出ている（向いていない）テーブルから作るのが基本です。  
今回の問題では、「顧客テーブル」から「請求テーブル」に矢印が向いているので、まずは「顧客テーブル」から作るようにしてください。  

　次に外部キーの見つけ方ですがこれはとても簡単です。  
2つのテーブルに共通するカラムがあれば、それが外部キーおよび主キーとなります。  
今回の問題では「顧客番号」がどちらも含まれていますので、  
「請求テーブル」の「顧客番号」が外部キー、「顧客テーブル」の「顧客番号」が主キーとなります。
外部キーは"テーブル名_ID"というで作ります。  

　最後に主キーの見つけ方です。主キーは内容が被ることなく、nullにもならないカラムでなければいけません。  
 多くの場合IDとなる番号が主キーです。  
今回の問題では「請求番号」がそれにあたります。  

## 余談
### 余談①

　これは応用情報技術者試験の問題を基に作成しています。  
応用情報技術者試験のほかに、「基本情報技術者試験」「ITパスポート」などの学生向けの資格があります。
[![](https://github.com/Cist-ProjectMember/ProjectMemberDocuments/blob/master/2020s/supplement/database/image/%E5%9B%B311.png)](https://www.jitec.ipa.go.jp/1_11seido/seido_gaiyo.html)  

　自宅にいる時間が多い今だからこそ、何か新しい資格を取ってみてはいかがでしょうか？  
気になる方がいましたら、[こちら](https://www.jitec.ipa.go.jp/1_11seido/seido_gaiyo.html)が公式サイトとなります。

### 余談②

　今度データベースを扱うにあたってJDBCを使用することが増えてくると思います。  
JDBCはJava側からデータベースを操作するためのものであり、  
これからは今回の講習のようにコンソールを直接いじってデータを追加することはなかなかありません。  
ぜひJSBCも使えられるようになりましょう。
