# opendata_analy
～政府調査スマホの利用の実態といじめの関係を分析してみた～

【分析概要】

１、全国の小学生～高校生を対象としたインターネット利用に関するアンケート（内閣府主管）と、暴力事件・いじめ・不登校といった教育課題（文科省主管）の間に関係性があるかどうかを分析する。　　　
２、１を踏まえて、各都道府県の傾向性をさぐる。

１の手法：重回帰分析を用いて、ネット利用アンケート（説明変数）の教育課題（目的変数）に対する寄与率や決定係数を確認する。
２の手法：因子分析を用いて、各都道府県の因子得点を求め、長所短所などを評価する。

【各ファイルの解説】
01質問リスト抽出／
e-statからダウンロードした生のCSVファイルは、１質問１ファイルなので、90あまりのファイルに分割されています。
これらのファイルから、質問内容や回答者数だけを抽出して一覧にまとめ、
どの質問項目を分析に使うかを検討します。\n  
02ファイル結合／


