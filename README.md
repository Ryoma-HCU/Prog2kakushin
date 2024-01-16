# Prog2kakushin

### プログラム 1 について
- **どういうプログラム(概要)**  
乱数から自動的に正規分布に従うデータを作り，その母集団からサンプリングし，標本を母集団を比較することで母集団推定の精度や入力値による推定変化を視覚的に分かりやすく表示する．  
ただし，<ins>可能な限り数値推定はライブラリを利用せず</ins>，授業内や自分で学習した内容・公式で導出する．  
プログラムは下記の式に従い母集団推定を行う．  
1. 標本数が30以上かつ母標準偏差が既知の場合：正規分布  
   ($\mu$:母平均, $\sigma$:母標準偏差, $n$:標本数, $\bar{x}$:標本平均, $Z$:標準正規分布確率密度)
$$\bar{x}-Z\frac{\sigma}{\sqrt{n}} \leq \mu \leq \bar{x}+Z\frac{\sigma}{\sqrt{n}}$$
2. 標本数が30未満または母標準偏差が不明の場合：t分布・χ²分布  
  ($s$:標本標準偏差, $t$:t分布確率密度, $\chi^{2}$:χ²分布確率密度)  
$$\bar{x}-t\frac{s}{\sqrt{n}} \leq \mu \leq \bar{x}+t\frac{s}{\sqrt{n}}$$
$$s\sqrt{\frac{n-1}{upper\chi^{2}}} \leq \sigma \leq s\sqrt{\frac{n-1}{lower\chi^{2}}}$$

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
音声データを $f(t)$ とすると，
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
調べたい音声の時間帯と周波数帯の上限・下限を入力後，単位変換を行い積分計算を実行し，その結果である周波数波形グラフと最大の振幅を持つ周波数・振幅の表示と，入力した時間帯を強調した元の時間波形グラフを合わせて表示出力．  

- **工夫した点**  
まず，計算上は単位がHz(ヘルツ)やs(秒)よりもデータ個数に合わせた自然数が好ましいが，ユーザの利便性の観点から適当な自然数よりも現実世界で使えるHzやsの入力を受け付ける様に単位変換を定義した．  
また，関数形で表すことができる数値データは関数f(t)のもと積分が用意だが，アップロードされる音声ファイルは関数形で表現できないものがほとんどであるため，<ins>積分ライブラリも導入せず，台形公式に基づき近似積分をfor文で実現した</ins>．  
これにより，データの分割とそれに伴う計算過程が明示され，よりこの分野に対する理解が深まり学習にも有効である．  
そして，ユーザがどの範囲を調査しているのか分かるようにするため，元グラフの入力した時間範囲を薄い塗りつぶしで強調し，計算結果の周波数で最も振幅が大きい箇所も線引きで強調することで，視覚的に分かりやすい解析結果を提示している．  

- **注意事項**  
このプログラムは高速で計算することを目的としておらず，広すぎる周波数帯域または調査範囲時間を入力すると計算に時間がかかってしまう．  
よって，広周波数帯域調査の場合は調査範囲時間を，広調査範囲時間の場合は周波数帯域をそれぞれ狭める必要がある．  
Ex. 周波数帯域：1～10000 Hz　調査範囲：0～0.1 s  

### プログラム 3 について
- **どういうプログラム(概要)**

- **どんな状況で役に立つのか？ (なぜこれを作ったのか？)**

- **入力と出力**

- **工夫した点**
