# opendata_analy
～政府調査スマホの利用の実態といじめの関係を分析してみた～

【分析概要】

１、全国の小学生～高校生を対象としたインターネット利用に関するアンケート（内閣府主管）と、暴力事件・いじめ・不登校といった教育課題（文科省主管）の間に関係性があるかどうかを分析する。　
２、１を踏まえて、各都道府県の傾向性をさぐる。

１の手法：重回帰分析を用いて、ネット利用アンケート（説明変数）の教育課題（目的変数）に対する寄与率や決定係数を確認する。
２の手法：因子分析を用いて、各都道府県の因子得点を求め、長所短所などを評価する。

最終的なレポート資料はこちら↓

https://drive.google.com/file/d/1HQKeW5Ng7E08MeFPu1sak5aIyZK_FeHu/view?usp=sharing 
（このGit Hubリポジトリでは、14～25シート、33～36シートのコードは省略しています。）

【利用したデータ】

青少年のインターネット利用環境実態調査
　https://www8.cao.go.jp/youth/youth-harm/chousa/net-jittai_list.html
　H26～H29の４カ年分、内閣府主管、都道府県単位など
　概要：スマホなどの利用状況や家庭内ルール、危険性の学習機会について
　対象者：小中高校生をほぼ均等に抽出
  利用したデータの単位：パーセント（都道府県ごとに、回答者数のうちYESと回答した人の割合）

児童生徒の問題行動・不登校等生徒指導上の諸課題に関する調査
　http://www.mext.go.jp/b_menu/houdou/30/10/1410392.htm
　H19～H29の11カ年分、文科省主管、都道府県単位など
　概要：暴力事件、いじめ、不登校などの1000人あたりの件数
　対象：小中高の合算（不登校は小中と高校で分かれている→２：１で加重平均）
  データの単位：生徒1000人あたりの発生人数（都道府県ごと）

（いずれもデータはE-statよりダウンロード可能）



【各ファイルの解説】

01質問リスト抽出／
e-statからダウンロードした生のCSVファイルは、１質問１ファイルなので、90あまりのファイルに分割されています。
これらのファイルから、質問内容や回答者数だけを抽出して一覧にまとめ、
どの質問項目を分析に使うかを検討します。

02ファイル結合／
01の作業で、アンケートの項目（質問文）と回答者数をリスト化しました。このリストを精査し、回答者数が十分な項目だけを抽出し、１つのデータフレームに結合します。

以上、01と02の作業を４カ年分行い、同じ質問項目を抽出した上で、１つのデータフレームに結合します。
結合の方法は、行に追加（axis=0）したので、４７都道府県×４カ年＝１８８レコード、となります。
ただし、１人も調査がなされていない都道府県（0値のセル）がいくつかありましたので、それらを削除すると最終的には１８５レコードとなりました。

03重回帰分析／
02のファイル４カ年分を結合したデータを利用して、重回帰分析を行います。02で質問項目を絞りましたが、さらに03では解答項目を絞ります。その後、重回帰分析にかけ、決定係数からあてはまり度を確認します。スマホアンケートが説明変数で、暴力事件・いじめ認知・不登校件数が目的変数ですので、３つの結果を確認します。

＜分析の結果＞不登校件数とスマホ利用の分析結果では、自由度修正済み決定係数が0.969と、非常に高い値を示していることがわかりました。スマホ利用のルールや習慣が、引きこもったり、学校生活で人間関係に折り合いをつけることが難しくなる傾向になったりするのは、人間の感覚的にも納得のいく結果が出たように思われます。

質問項目をその内容から判断して、２つのグループに分けました。１つ目は、本人の行動にかかわる質問項目です。例えば、「悪口等のメール・メッセージ送った」、「掲示板で自分や他人の情報書き込んだ」などの質問です。２つ目は、周囲の環境にかかわる質問項目です。例えば、「メール・メッセージを送る相手の制限」、「（スマホのことについて）兄弟・姉妹から教えてもらった」などの質問が挙げられます。


  
 




