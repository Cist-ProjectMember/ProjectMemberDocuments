# データベース課題
## 課題
次の図を見て、2つのテーブルを作成せよ。
ただし、データ型及び列制約は自分で考察すること。    
<img width="500" alt="illust1" src="https://github.com/Cist-ProjectMember/ProjectMemberDocuments/blob/master/2020s/supplement/database/image/%E5%9B%B310.png">

図1．販売管理システムのE-R図

## 解説
今回の課題は、データ型と列制約を理解しているかがカギとなります。  
これから成果物を作るにあたって、データベースを使用する学生は多いと思います。  
データベースを作るにあたって、まずはデータ型と列制約について練習しましょう。  

### データ型
データ型は宗教問題になりかねになりかねないので、あくまで例として確認ください。  
講習会でも説明した通り、データ型は大きく分けて以下のように区別することができます。  
<img width="500" alt="illust1" src="https://github.com/Cist-ProjectMember/ProjectMemberDocuments/blob/master/2020s/supplement/database/image/%E5%9B%B33.png">

　今回はこの図に書かれている型のみで作ります。  
今回の課題で悩むカラムは「請求書番号」「顧客番号」の番号関連、  
「請求日」「形状年月」の日付関連の2点だと思います。  
　まずは番号について、番号は学籍番号のように「b21○○○○○」のように数字以外の文字を使うことがよくあります。  
今回は指定がなかったため、おそらく"INTEGER"などを使用した学生も多いと思います。  
どちらが正しいなどはないですが、"CHAR"を使うことがあることも覚えておきましょう。
　次に日付関連です。日付には"DATETIME", "DATE", "TIME"など数多くの方が存在します。  
どれが優れているなどの優劣はありませんがほげほげ

## 余談
これは応用情報技術者試験の問題を基に作成しています。  
応用情報技術者試験のほかに、「基本情報技術者試験」「ITパスポート」などの学生向けの資格があります。
<img width="500" alt="illust1" src="https://github.com/Cist-ProjectMember/ProjectMemberDocuments/blob/master/2020s/supplement/database/image/%E5%9B%B311.png">

自宅にいる時間が多い今だからこそ、何か新しい資格を取ってみてはいかがでしょうか？  
気になる方がいましたら、[こちら](https://www.jitec.ipa.go.jp/1_11seido/seido_gaiyo.html)が公式サイトとなります。
