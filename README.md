# Prog2kakushin

## プログラム 1 について
- どういうプログラム(概要)

乱数から自動的に正規分布に従うデータを作り，その母集団からサンプリングし，標本を母集団を比較することでその精度や入力値による変化を視覚的に分かりやすく表示する．


- どんな状況で役に立つのか？ (なぜこれを作ったのか？)

ここでは現実の正規分布に従うデータを疑似的に作りあげたが，この母集団推定プログラムは調査対象全てを調べることが困難な場合や，サンプル数が少ない場合など，限られた情報の中から母集団の特徴量を推測し，欲しい情報を現実のデータからも得ることができる．
このプログラムの作成の経緯として，先日学習した実社会指向基礎数学の統計学分野で，限りある情報から全体を推測できる統計学の計算をPythonプログラムでも作ってみようと思い至ったことから．


- 入力と出力

入力された母平均・母標準偏差により生成された乱数の母集団から，入力された回数標本抽出を行い，入力された信頼度・母標準偏差の使用の有無の決定を元に母集団の平均・標準偏差・範囲をデータフレームで出力し，母集団と標本のヒストグラムと正規分布曲線をグラフで出力する．
- 工夫した点
可能な限り実社会指向基礎数学の統計学分野で習った内容を元に，Pythonに元から導入可能なライブラリを必要最低限(標準正規分布の確率密度の計算など)だけ使用して，残りはその講義で習った計算式を元に値を出力した．
またその講義でも扱っていない，標本数が少ないまたは母標準偏差が分からない場合の母集団推定に用いるt分布やχ²分布も自学習し，可能な限り計算式だけで導出できる様にプログラムした．


## プログラム 2 について
- どういうプログラム(概要)

- どんな状況で役に立つのか？ (なぜこれを作ったのか？)

- 入力と出力

- 工夫した点


## プログラム 3 について
- どういうプログラム(概要)

- どんな状況で役に立つのか？ (なぜこれを作ったのか？)

- 入力と出力

- 工夫した点
