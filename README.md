# Prog2kakushin

### プログラム 1 について
- **どういうプログラム(概要)**  
乱数から自動的に正規分布に従うデータを作り，その母集団からサンプリングし，標本を母集団を比較することで母集団推定の精度や入力値による推定変化を視覚的に分かりやすく表示する．  
ただし，<ins>可能な限り数値推定はライブラリを利用せず</ins>，授業内や自分で学習した内容・公式で導出する．  

- **どんな状況で役に立つのか？ (なぜこれを作ったのか？)**  
ここでは現実の正規分布に従うデータを疑似的に作りあげたが，この母集団推定プログラムは調査対象全てを調べることが困難な場合や，サンプル数が少ない場合など，限られた情報の中から母集団の特徴量を推測し，対象集団の情報提供やそれに伴う意思決定にも役立てることができる．  
また，数値推定ライブラリを利用せずほとんど利用せず計算式で導出しているため演算の内容が確認でき，統計学を間庭媚態ときの学習プログラムとしても役に立つ．  
このプログラムの作成の経緯として，先日学習した実社会指向基礎数学の統計学分野で，サンプル情報から全体を推測できる統計学の計算をPythonプログラムでも作ってみようと思い至ったことから．  

- **入力と出力**  
入力された母平均・母標準偏差により生成された乱数の母集団から，入力された回数標本抽出を行い，入力された信頼度・母標準偏差の使用の有無の決定を元に母集団の平均・標準偏差・範囲をデータフレームで出力し，母集団と標本のヒストグラムと正規分布曲線をグラフで出力する．  

- **工夫した点**  
可能な限り実社会指向基礎数学の統計学分野で習った内容を元に，Pythonに元から導入可能なライブラリを必要最低限(標準正規分布の確率密度の計算など)だけ使用して，残りはその講義で習った計算式を元に値を出力した．  
またその講義でも扱っていない，標本数が少ないまたは母標準偏差が分からない場合の母集団推定に用いるt分布やχ²分布も自分で学習し，可能な限り計算式だけで導出できる様にプログラムした．  

### プログラム 2 について
- **どういうプログラム(概要)**  
colabにアップロードされた音声ファイルを読み込み，その音声ファイルにフーリエ変換を適応することで，時間変化に伴う音の波形関数を周波数に伴う波形関数に変換し，アップロードされた音声ファイルの音の高さと大きさを分析する．  
ただし，<ins>フーリエ変換ライブラリは一切使用しない</ins>．  
フーリエ変換は音に限らず様々な数値データをcos波/sin波に分解でき，計算が速い高速フーリエ変換(FFT)など存在するが，  
このプログラムでは下記の式に従い時間領域から周波数領域に変換する．  
音声データをf(t)とすると，
$$f(t)=\frac{a_{0}}{2} + \sum_{n=1}^\infty(a_{n}\cos(\frac{2\pi nt}{T})+b_{n}\sin(\frac{2\pi nt}{T}))$$
音声データは上記の右辺より，様々な係数($a_{n}$, $b_{n}$)を持つ様々な周波数($\frac{n}{T}$)の三角関数(cos, sin)で表現可能である事を意味している．
このとき各周波数における波の振幅は，
$$a_{n}=\frac{2}{T}\int_{0}^{T}f(t)\cos(\frac{2\pi nt}{T})dt$$
$$b_{n}=\frac{2}{T}\int_{0}^{T}f(t)\sin(\frac{2\pi nt}{T})dt$$
であり，この係数を元に音声解析を行う．

- **どんな状況で役に立つのか？ (なぜこれを作ったのか？)**  
アップロードした音がどの程度の周波数(音の高さ)をどれだけの量(その大きさ)含むかを視覚的に分かりやすく表示するので，音声解析を行いたい場合に役立つ．  
例えば，物体の衝突音はその音の高さと衝突エネルギーに比例するため，そのエネルギーを計測できなくともある程度音から推測できる．  
また，人の声から性別を判断したい場合，男性声と女性声の周波数は分かれるため，ある程度性別判定の目安を付けられる．  
そして，このプログラムではあえてフーリエ変換ライブラリを利用しておらず，計算の内容をフーリエ変換の定義に基づき実際に演算をしているため，フーリエ変換を学びたい場合にも，参考プログラムとして利用できる．  
このプログラムを作った経緯としては，プログラミングⅡ講義のNumpyを使った発展課題にてフーリエ級数展開が取り上げられていたため興味を持ち，自分である程度学習してPythonで自力で計算機構を作り，フーリエ変換が確かなものか確認したいと思ったことから．  

- **入力と出力**  
解析したい音声ファイルをアップロードしそのファイル名と拡張子名を入力後，読み込んだ音声ファイルの時間波形グラフを出力．  
調べたい音声の時間帯と周波数帯の上限・下限を入力後，単位変換を行い積分計算を実行し，その結果である周波数波形グラフと，入力した時間帯を強調した音声ファイルの時間波形グラフと合わせて出力表示．  

- **工夫した点**


### プログラム 3 について
- **どういうプログラム(概要)**

- **どんな状況で役に立つのか？ (なぜこれを作ったのか？)**

- **入力と出力**

- **工夫した点**
