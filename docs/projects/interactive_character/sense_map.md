# 感覚マップと物理エンジンを使ったAIエージェントへの皮膚感覚の実装
## AIエージェントにおける皮膚感覚の実装の必要性
人にも動物にも皮膚感覚があり、
皮膚感覚はおそらく、振動、温度、痛みなどを感じて、危険や環境の変化に対応をするという用途や、物を持ったり力加減をするのに使われています。
また、個体同士のコミュニケーションにも重要で、
個体コミュニケーション用途の皮膚感覚実装を考えます。

まずは、ふわみくに猫と似たような皮膚感覚のような物を実装して、
スキンシップコミュニケーションを実現したいと思います。

動物の分類や個体差によって、触る場所、力、動きによって気持ちいいor不快などの気持ちが生じるはずで、そのAIが感じるであろう感覚を計算したり、個体ごとに設定する方法を考えます。

## 皮膚感覚の設計
皮膚の下の痛覚と神経細胞の電気信号をシミュレートしたりとか、神経レベルでのシミュレートは厳しい。なので、物体表面に対する力Fの時系列データを入力として、
どういった感覚が生じるかを計算するモデルやアルゴリズムを作る方向で行きます。

皮膚感覚は[圧力の強さや圧力の強さの変化を感知する器官](https://bsd.neuroinf.jp/wiki/%E4%BD%93%E6%80%A7%E6%84%9F%E8%A6%9A)で成り立っているようです。
スキンシップで重要なのは経験上どちらかというと圧力変化だと思うので、
こちらを優先して、実装してみることにします。

まずは、圧力変化を検知した位置で、圧力の値に対して、
どう感じるかをマッピングするというシンプルなものにします。

モデルごとにメッシュごとにFの範囲を設定する。

* 快適F下限
* 痛いF下限

の２つのマップを作ります。

!!! todo
    * 圧力の強さがかかり続けることは重要？
    * 強さに対する関数？
    * ある程度長い時系列を見ないと検知できないことってある？

## 皮膚感覚の実装
### 感覚編集エディタの実装
AI作成者が感覚のパラメータを調整するためのエディタ。

* 3Dモデルのメッシュにタッチしてレイと交差したメッシュに色を塗る感じにする。
* 回転機能と保存機能を実装する。
* (optional) 服とか装飾品を除外する？服とかに触覚があるキャラもあるかも。

体内部の感覚など、他のメッシュで隠れている部分を編集できるようなモードも用意する必要がある。例えば、メッシュを展開したものにテクスチャを貼り付けて、それに感覚マップをつけていくなど。

!!! todo
    * この情報を付与するのを自動化したい。
    * メッシュに対するセマンティックセグメンテーション相当は、
    * メッシュに紐づいたテクスチャに対してセマンティックセグメンテーションする。
    * テクスチャにすると情報が落ちるので、レンダリング結果に対してかけるとか。

### 皮膚への力変化の計算
皮膚感覚をシミュレートするためには、触るという動作を検知したり、
力のかかり具合を計算する必要があり、今の所、物理エンジンに頼るのが最も楽です。

!!! todo
    * 実装する。
    * 人の感覚とVR空間の力加減は一致するか？

### 感覚への反応
表情や体の動きといった反射的な動きと、長期的な気持ちへの影響をモデル化する必要がある。
