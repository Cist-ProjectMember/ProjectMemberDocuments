# データベース演習課題の解答
## 演習１
1. 表1のテーブル構造情報を基に、student_grade_informationを作成し、表2のデータを入れなさい。その後、テーブルのデータを表示しなさい。
* student_grade_informationを作成
```SQL
create table student_grade_information(
    id integer,
    student_name varchar(8),
    math_score integer,
    english_score integer
);
```
* データを挿入
```SQL
insert into student_grade_information(id, student_name, math_score, english_score)
    values (1,'A',60,60),
           (2,'B',80,80),
           (3,'C',0,0);
```
* テーブルを表示
```SQL
select * from student_grade_information;
```
***
2. math_scoreを基準に降順でソート
```SQL
select *from student_grade_information
order by math_score desc;
```
## 演習2
1. 表3のテーブル構造情報をもとにsales_historyを作成し、表4の情報を入れなさい。その後、テーブルのデータを表示しなさい。
* sales_historyを作成
```SQL
create table sales_history(
    id integer,
    product_name varchar(16),
    price integer,
    date DATE
);
```
* データを挿入
```SQL
insert into sales_history(id, product_name, price, date)
    values  (1,'マスク',500,20200401),
            (2,'マスク',500,20200401),
            (3,'トイレットペーパー',200,20200402),
            (4,'トイレットペーパー',200,20200402),
            (5,'消毒液',300,20200403),
            (6,'消毒液',300,20200403),
            (7,'マスク',500,20200404),
            (8,'空気除菌剤',5000,20200404),
            (9,'タンポポ茶',10000,20200405),
            (10,'タンポポ茶',10000,20200405);
```
* テーブルを表示
```SQL
省略
```
***
2. マスクが売れた日の日付を表示しなさい。
```SQL
select date from sales_history
    where product_name='マスク';
```
***
3. 20200403から20200405のデータをすべて表示しなさい。
```SQL
select * from sales_history
    where 20200403<=date and date<=20200405;
```
または、
```SQL
select * from sales_history
    where date BETWEEN 20200403 and 20200405;
```
***
4. 空気除菌剤のpriceを100に更新しなさい。
```SQL
update sales_history
  set price=100
  where product_name='空気除菌剤';
```
***
5. タンポポ茶を販売したデータをすべて削除しなさい。
```SQL
delete from sales_history
  where product_name='タンポポ茶';
```
## 演習３
1. 表5のテーブル構造情報をもとにstudent_informationを作成し、表6の情報を入れなさい。その後、テーブルのデータを表示しなさい。
* student_informationを作成
```SQL
create table student_information(
    student_number integer primary key,
    name varchar(8) not null
);
```
* データを挿入
```SQL
insert into student_information(student_number, name)
    values (1,'a'),
           (2,'b'),
           (3,'c'),
           (4,'d'),
           (5,'e');
```
* テーブルを表示
```SQL
省略
```
***
2. 表7のテーブル構造情報をもとにchoice_electivesを作成し、表8の情報を入れなさい。なお、student_informationのstudent_numberを親カラムとし、choice_electivesのstudent_numberを子カラムとしたforeign key制約も設定しなさい。参照制約動作は親カラムが削除されたら追従する。
* choice_electivesを作成
```SQL
create table choice_elevtives(
    student_id integer primary key,
    electives_1 varchar(8) not null,
    electives_2 varchar(8) not null,
    foreign key (student_id)REFERENCES student_information(student_number)
    ON DELETE CASCADE
);
```
* データを挿入
```SQL
insert into choice_elevtives(student_id, electives_1, electives_2)
    VALUES (1,'数学','英語'),
           (2,'英語','数学'),
           (3,'英語','数学'),
           (4,'物理','化学'),
           (5,'生物','化学');
```
* テーブルを表示
```
省略
```
***
3. electives_1が英語のデータを表示しなさい。なお、student_information(student_number,name)、choice_electives(electives_1,electives_2)を表示させること。
```SQL
select student_information.student_number,student_information.name,choice_elevtives.electives_1,choice_elevtives.electives_2
    from student_information inner join choice_elevtives on student_information.student_number = choice_elevtives.student_id
    where choice_elevtives.electives_1='英語';
```
***
4. student_informationからidが5のタプルを削除しなさい。その後、choice_electivesから、idが5のタプルが消えていることを確認しなさい。
* タプルを削除
```SQL
delete from student_information
  where student_number=5;
```
* choice_electivesテーブルを表示
```SQL
select * from choice_elevtives;
```
