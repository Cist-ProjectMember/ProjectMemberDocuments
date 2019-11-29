# JDBC

## JDBC (Java Database Connectivity)

ソフトウェア内のプログラムからデータベースを利用するには、ネットワーク技術を介してDBMSに接続し、クエリを実行する必要がある。</br>
Javaではこうした操作を行うための橋渡しとなる部分(ドライバ)用のクラスとして用意されるJDBCを利用する。</br>
つまり、Java経由でデータベースを操作するにはJDBCを利用するということである。</br>


## 前準備
[ここ](https://jar-download.com/artifacts/com.h2database/h2/1.4.196/source-code)からh2-1.4.196.jarをダウンロードし、zipファイルを展開する。</br>
新規ディレクトリーからlibを作成し、その中に展開したフォルダ内のjarファイルをドラッグ&ドロップする。</br>
左上のファイルからプロジェクト構造を選択し、モジュール内の依存関係をクリック、右(Macなら下)側にある「+」からjarまたはディレクトリーを選択し、jarファイルを追加する。(これらの作業は注意を確認しながらしてください)。</br>
その後、プロジェクト名を右クリックし、再ビルドをする。</br>
#### 注意
/*image*/


## JavaからDBMSにアクセスする

```
try {
  Class.forName("org.h2.Driver");
} catch(ClassNotFoundException e) {
  e.printStackTrace();
} try (Connection connection = DriverManager.getConnection("jdbc:h2:~/h2db/lecture;Mode=PostgreSQL;　AUTO_SERVER=TRUE;", "設定したユーザー名", "設定したパスワード"); Statement statement=connection.createStatement()){
// その他の処理(JavaからDBMSにアクセス-2へ続く...)
} catch(SQLException e) {
     e.printStackTrace();
}
```
```
String sql = “SQL文”;
SELECT以外の場合
statement.executeUpdate(sql);
SELECTの場合
ResultSet result = statement.executeQuery(sql);
while(result.next()) {
String 変数名 = result.getString(“カラム名”)//文字列型の場合
		int 変数名 = result.getInt(“カラム名”)//Int型の場合
}
```


## テーブルの削除

テーブルはDROPステートメントで削除する。</br>
例：`drop table テーブル名;`</br>
　※dropはテーブル、deleteはタプルを削除することに注意。
　※テーブルが存在しない状態で使うとエラーが発生する。
　※テーブル名の前にif existsを入れるとテーブルが存在しないときに実行されなくなる。


## 演習課題

### 課題1
データベースにSTUDENTS_INFORMATION3テーブルを作成し、以下のデータをJavaで入れなさい。

|名前   |学籍番号  |出席番号|
|:-----|---------|:-----:|
|山田太郎|b2190001|53     |
|鈴木一郎|b2190002|64     |

### 課題2
JavaでSTUDENTS_INFORMATION3の山田 太郎の学籍番号と出席番号をそれぞれ、`b2191001`、`76`に変更しなさい。</br>
また、鈴木一郎を削除しなさい。</br>

### 課題3
STUDENTS_INFORMATION3に新たに以下のデータを追加しなさい。

|名前     |学籍番号 |出席番号|
|:-------|--------|:-----:|
|Bob     |b2181998|99     |
|Jhon    |b2181999|100    |
|名無権兵衛|b2182000|10     |

JavaでSTUDENTS_INFORMATION3の中から出席番号が50以降の学生を、出席番号が降順になるように検索/表示しなさい。</br>
