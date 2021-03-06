# エージェントに褒められる効果
## 雑フローチャート
https://twitter.com/_xiongjie_/status/1348521913253982210

![](praising_agent/agent_design.png)

とにかく、褒める。悪くとも中性的なコメントで終わらせることが重要のようです。ただ、ここで扱われているタスクは数字をある順番で押していくだけのもので、単純なタスク、ストレス負荷が高いタスクであり、エンジニアが取り組む、知的作業とは性質が異なる可能性がある。ただ、想像作業も単純作業の積み重ねであり、プログラミングもタイピング、計算などの積み重ねであることを考えると、効果はあるのかもしれない？

## パフォーマンス指標
* リポジトリのコード量(タイピング量?)
* 文章書いた量
* 勉強した量

## コード量、文章書いた量の把握
* コミット数
* 前回のコミットとの差分を計測
* ファイルの種類により、文章、コード、画像に分類して褒める。
* 文字数、行数が増えたら褒める。
* いいねを得たツイート数も褒められる
* githubのスター数
* 勲章を出してくれるサービスをパクる。

## 1w: 集中力が上がるか実験 & 褒めるバリエーションを増やす
### ファイルの種類によって見る点を変える
文章：文字数
drawio: パースして図形数
コード：行数、関数、クラス数

データの持ち方を変える

スケジューラーのレジューム機能ほしい。起動してから１時間だと微妙。

### スターアニスちゃん
**効果音で画面に気をひきつけてから、
モーションと文字で褒めてくれる。**
ハートを出して褒めてくれる。
https://soundeffect-lab.info/

### 褒めアーキテクチャ
褒める候補を探すクラスが複数あって、
そこからランダムに？
でも、よく見てくれてる感がある方がいいので、
うまくランキング付するようにする。スコアを計算する。
（同じ褒め方は１ヶ月に一回までという成約を入れる）
各種褒めに関して、最後に使った日を入れる。
文言が完全に一致しているかチェックだけする。

yamlとかで文言、比較基準を管理して、その中から選ぶ。
ハッシュを入力とする。

DONE
コミットハッシュ：abbc538359a0442202c3829f962e63975cbc5662

指標を計算したりするところが一番難しくて、
褒めるところは単に設定ファイルだけで行けそう。
指標計算あたりのクラス設計をしっかりする。

### 方針
褒める対象を増やすか、
いいのを思いついたら書くか。
いろいろな視点で同じことを褒めるようにするか?

### 筋肉トレーニングの回数をチェックして褒めてくれる
holisticグラフを使う。

### 座りすぎチェック
カメラ配置に依存。オクルージョンがあると厳しいのでは。
時系列から予測する？
立つ→かがむ→すわるだから座っているはず。とか。

やはり、学習ベースでやるのがいい？
座っている。立っている状態のデータを集めて、
そこから、人工的にオクルージョンさせてそのデータで学習させる。

### デザインコンセプト
嫁というより、パートナーを作りたい。