# Prog2kakushin

### プログラム 1 について
- **どういうプログラム(概要)**  
乱数から自動的に正規分布に従うデータを作り，その母集団からサンプリングし，標本と母集団を比較することで母集団推定の精度や入力値による推定変化を視覚的に分かりやすく表示する．  
ただし，<ins>推定値導出ライブラリの使用を確率密度(Z,t,χ²)のみに限定</ins>し，講義や自分で学習した内容・公式で導出する．  
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
また，数値推定ライブラリをほとんど利用せず計算式で導出しているため演算の内容が確認でき，統計学を学びたいときの学習プログラムとしても役に立つ．  
このプログラムの作成経緯として，先日学習した実社会指向基礎数学の統計学分野で，サンプル情報から全体を推測できる統計学の計算をPythonプログラムでも作ってみようと思い至ったことから．  

- **入力と出力**  
入力された母平均・母標準偏差により生成された乱数の母集団から，入力された回数標本抽出を行い，入力された信頼度・母標準偏差の使用の有無の決定を元に母集団の平均・標準偏差・範囲をデータフレームで出力し，母集団と標本のヒストグラムと正規分布曲線をグラフで出力する．  

- **工夫した点**  
可能な限り実社会指向基礎数学の統計学分野で習った内容を元に，Pythonに元から導入可能なライブラリを必要最低限(確率密度値の参照など)だけ使用して，残りはその講義で習った計算式を元に値を出力した．  
またその講義でも扱っていない，標本数が少ないまたは母標準偏差が分からない場合の母集団推定に用いるt分布やχ²分布も自分で学習し，可能な限り計算式だけで導出できる様にプログラムした．  
加えて，出力形式をデータフレーム表を用いることで，母集団値とユーザの入力に基づき推定した標本値を見比べやすくしている．  

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
colabにアップロードされた画像ファイルを読み込み，隣接するピクセル(画素)間の縦/横それぞれの画素値の差をとり，それを新たな画像の画素値とすることで，アップロードされた画像のエッジ(境界線)を検出する．  
また入力された閾値以上のエッジのみを強調した画像表示をフィルタとしたり，出力画像の明度調節やエッジ検出後の各画素値に対する画素数もグラフ表示してユーザが見やすい分析結果を提示する．  
ただし，<ins>画像エッジ検出ライブラリは一切使用しない</ins>．なお，エッジ検出の詳細な考え方は以下の画像の通りである．  
![Edges Image](images/Edges.png)

- **どんな状況で役に立つのか？ (なぜこれを作ったのか？)**  
エッジ検出は画像内の捉えたい物体・人物の輪郭を強調表示するため，顔認証やAIの画像学習にも用いられている．  
また，人間の目では捉えることが難しいほど薄い輪郭や入り乱れた複雑な画像でも，このプログラムでは表示明度の調整や閾値によるフィルタ機能を備えているため分析を行いやすい．  
更に，各方向成分のエッジ検出の出力が特徴的な画像であるため，おしゃれな画像フィルタとしても利用できる．  
そして，このプログラムではあえてエッジ検出ライブラリを使用していないため，普段は計算内容が分からないライブラリ関数内部の過程が明示され，画像処理の基礎であるエッジ検出を学べる参考プログラムとしても利用できる．  
このプログラム作成の経緯としては，前回作成したフーリエ変換プログラムの自主学習の際に，画像データに対して微分を適応することでエッジ検出を行えることを合わせて知ったため，<ins>前回の積分計算とは対となる微分計算をここで行おう</ins>と思ったことから．  

- **入力と出力**  
分析したい画像ファイルをアップロードまたはサンプル画像からダウンロードし，拡張子がjpgのファイル一覧を表示しその中から分析したい画像名を1つ拡張子付きで入力．  
更にエッジ検出の閾値, 表示画像明度の倍数, 縦/横の各方向検出の有無を入力後，各方向の画素値の差を計算し，オリジナル画像, 各方向成分の閾値フィルタ画像と全体表示画像(縦横両方分析をした場合その2つの合成画像を更に表示), 各方向成分の画素値に対する画素数のグラフを合わせて表示出力．  

- **工夫した点**  
ただのエッジ検出プログラムではなく閾値によるフィルタや出力画像の明度調整機能を付けることで，分析結果をユーザが見やすいものになる様な機能を付与した．  
特に閾値によるフィルタでは閾値設定の基準になる様に，エッジ検出後の画像の画素値に対する画素数のグラフを領域塗りつぶしで表示することで，塗りつぶされた範囲の画素数のみが表示されている事を示す．  
また，エッジ検出をカラー画像での出力が可能かどうか検討するためのテストプログラムを作ったが，以下の画像の様にRGBそれぞれの色においてはっきり差が出る画像は現実世界の画像では殆ど無く，これを更に表示すると還って出力結果が見にくいものとなると判断したためあえて省略した．  
![Color Bars Image](images/Color_Bars.png)
