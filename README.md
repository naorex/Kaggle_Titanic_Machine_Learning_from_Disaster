# (kaggle) Titanic - Machine Learning from Disaster
Titanic - Machine Learning from Disaster コンペのリポジトリ

- directory tree
```
Kaggle_Titanic_Machine_Learning_from_Disaster
├── README.md
├── data         <---- gitで管理するデータ
├── data_ignore  <---- gitで管理しないデータ(モデルとか、特徴量とか、データセットとか)
├── nb           <---- 作成したノートブック
└── src_att      <---- .ipynb 以外のコード
```

## Basics
### Overview
これは伝説のタイタニックMLコンペティションです。機械学習コンペティションに挑戦するための最初の、そして最高のチャレンジです。また、Kaggleプラットフォームの仕組みを理解するのに最適な機会でもあります。<br>
コンペティションの目的は、機械学習を使ってタイタニック号の沈没で生き残った乗客を予測するモデルを作成することです。


### The Challenge
タイタニックの沈没は、史上最も悪名高い海難事故の一つです。<br>
1912年4月15日、処女航海中に、広く「不沈没」と考えられていたタイタニック号は、氷山と衝突して沈没しました。残念ながら、乗っていた全員分の救命ボートはなく、2224人の乗客と乗組員のうち1502人が死亡しました。<br>
生存にはある程度の運が絡んでいたようですが、一部の人々は他の人々よりも生存率が高かったようです。<br>
このチャレンジでは、旅客データ（名前、年齢、性別、社会経済的地位など）を使用して、「どのような人が生存率が高かったか？」という質問に答える予測モデルを構築することを求めています。

### What Data Will I Use in This Competition?
このコンペティションでは、名前、年齢、性別、社会経済的地位などの乗客情報を含む2つの類似したデータセットにアクセスできます。1つのデータセットはtrain.csv、もう1つのデータセットはtest.csvという名前です。<br>
train.csvには、乗船した乗客の一部（正確には891人）の詳細が含まれており、重要なことに、彼らが生き残ったかどうか（「正解」とも呼ばれます）が明らかになります。<br>
test.csvデータセットには同様の情報が含まれていますが、各乗客の「正解」は開示されません。これらの結果を予測するのはあなたの仕事です。<br>
train.csvデータ内のパターンを使用して、残りの418人の乗船客（test.csv内で見つかる）が生き残ったかどうかを予測します。

### [side note]
トレーニングセットは、機械学習モデルを構築するために使用されます。トレーニングセットについては、各乗客のアウトカム（別名「正解データ」）を提供します。モデルは、乗客の性別やクラスなどの「特徴」に基づいて構築されます。また、特徴エンジニアリングを使用して新しい特徴を作成することもできます。<br>
テストセットは、モデルが未知のデータに対してどの程度のパフォーマンスを発揮するかを確認するために使用されます。テストセットについては、各乗客の正解データは提供されません。これらのアウトカムを予測するのはあなたの仕事です。テストセット内の各乗客について、トレーニングしたモデルを使用して、タイタニック号の沈没を生き延びたかどうかの予測を行います。<br>
また、すべての女性乗客のみが生き残ると仮定した予測のセットであるgender_submission.csvも、提出ファイルの例として含まれています。<br>
分かりやすく言うと、トレーニングセットはモデルを教えるためのデータ、テストセットはモデルの性能を評価するためのデータです。<br>gender_submission.csvは、女性乗客のみが生き残ると仮定した予測例です。


### Submission File Format
KaggleのTitanicコンペティションへの提出ファイルは、ヘッダー行を含めて418行のCSVファイルでなければなりません。<br>PassengerIdとSurvived以外の列や行が含まれている場合、提出はエラーになります。<br>
ファイルは、以下の2つの列で構成されている必要があります。<br>

- PassengerId (ソート順序は任意)
- Survived (生存者は1、死亡者は0で表されるバイナリ予測値)

補足として、PassengerIdは乗客のID番号、Survivedは生存したかどうかを示す列です。バイナリ予測値とは、0か1の2つの値のみを取る予測値のことです。

### train.csv colomn infomation
notebook: nb001<br>
891行、12カラム

|name|dtype|description|
|----|----|----|
|PassengerId|int64|乗客毎の固有ID|
|Survived|int64|死亡0、生存1のブール値|
|Pclass|int64|1,2,3のカテゴリ変数。1stクラス～3rdクラス|
|Name|object|重複なし。乗客名。敬称は17種類|
|Sex|object|男女2種類のみ。性別|
|Age|float64|null 177件。88種類。年齢|
|SibSp|int64|7種類。0,1,2,3,4,5,8ののカテゴリ変数。同乗した兄弟または配偶者の人数|
|Parch|int64|7種類。0,1,2,3,4,5,6のカテゴリ変数。同乗した親または子供の人数|
|Ticket|object|681種類。番号や文字列が混在。規則性や意味は不明。チケット番号|
|Fare|float64|248種類。運賃価格|
|Cabin|object|null 687件。147種類。英大文字+数字の組み合わせ。部屋番号|
|Embarked|object|null 2件。3種類。S,C,Qのカテゴリ変数。乗船した港。C = Cherbourg, Q = Queenstown, S = Southampton|

### test.csv colomn infomation
notebook: nb001<br>
418行、11カラム<br>
kaggleへのsubmit用のテストデータ。train.csvからSurvived列が消えたのみ。

|name|dtype|description|
|----|----|----|
|PassengerId|int64|同上|
|Survived|int64|同上|
|Pclass|int64|同上|
|Name|object|同上|
|Sex|object|同上|
|Age|float64|null 86件。同上|
|SibSp|int64|同上|
|Parch|int64|同上|
|Ticket|object|同上|
|Fare|float64|同上|
|Cabin|object|null 327件。同上|
|Embarked|object|null なし。同上|

### gender_submission.csv colomn infomaiton
notebook: nb001<br>
418行、2カラム<br>
女性乗客のみに絞り生存結果を推定した回答例。（答えではない）


## Log
### 20230922
- nb001
  - カレーちゃん著『Kaggleのチュートリアル第6版』に基づいて作成。
  - 与えられたデータ内容の確認。

  - 死亡者、生存者の人数<br>
  死亡0 : 549 (61.6%)<br>
  生存1 : 342 (38.4%)<br>
  全体 : 891<br>
  <img src='.\data\images\readme\nb001_Survived.png' width='500'>

  - 性別<br>
  男性は、死亡者0 が 生存者1 の約5倍<br>
  女性は、死亡者0 が 生存者1 の約3割ほどのみ<br>
  【気付き】 女性や子供から優先的に救命艇へ乗せられたため？<br>
  <img src='.\data\images\readme\nb001_Sex_Survived_table.png'><br>
  <img src='.\data\images\readme\nb001_Sex_Survived.png' width='500'>

  - チケットクラス<br>
  1stクラスの乗客の生存率が、3rdクラスの乗客より高い<br>
  <img src='.\data\images\readme\nb001_Pclass_Survived_table.png'><br>
  <img src='.\data\images\readme\nb001_Pclass_Survived.png' width='500'>

  - 年齢の分布<br>
  乳幼児から子供が数十人乗船しており、大人は10代後半～30代後半が多い<br>
  また、乳幼児から子供は生存率が高い<br>
  <img src='.\data\images\readme\nb001_Age_Survived_table.png'><br>
  <img src='.\data\images\readme\nb001_Age.png' width='500'><br>
  <img src='.\data\images\readme\nb001_Age_Survived_0.png' width='500'><br>
  <img src='.\data\images\readme\nb001_Age_Survived_1.png' width='500'><br>

  - 兄弟・配偶者の数<br>
  "0" のカテゴリーが大半を占め、次点で "1" のカテゴリー<br>
  <img src='.\data\images\readme\nb001_SibSp.png' width='500'><br>
  "2" 以上のカテゴリーをグループ化し、死亡・生存を確認<br>
  兄弟または配偶者が1人の場合の生存率が高い<br>
  <img src='.\data\images\readme\nb001_SibSp_table.png'><br>
  <img src='.\data\images\readme\nb001_SibSp_group.png' width='500'>

  - 両親・子供の数<br>
  "0" のカテゴリーが大半を占める。"3" 以上のカテゴリーはほぼ無し<br>
  <img src='.\data\images\readme\nb001_Parch.png' width='500'><br>
  "3" 以上のカテゴリーをグループ化し、死亡・生存を確認<br>
  両親または子供が1人の場合の生存率が高い<br>
  <img src='.\data\images\readme\nb001_Parch_table.png'><br>
  <img src='.\data\images\readme\nb001_Parch_group.png' width='500'>

  - 1人で乗船か、2人以上で乗船か<br>
  1人で乗船の死亡率が高い<br>
  <img src='.\data\images\readme\nb001_IsAlone_table.png'><br>
  <img src='.\data\images\readme\nb001_IsAlone.png' width='500'>

  - 運賃<br>
  大半の乗客は運賃100 以下<br>
  運賃が高くなるにつれ、生存率が高い<br>
  <img src='.\data\images\readme\nb001_Fare_table.png'><br>
  <img src='.\data\images\readme\nb001_Fare.png' width='500'>

  - 名前<br>
  敬称の種類は17種類<br>
  <img src='.\data\images\readme\nb001_Name_Surname.png'><br>
  年齢の平均値。"Master" の平均値が1桁のため、子供の愛称的な敬称と思われる<br>
  <img src='.\data\images\readme\nb001_Name_AverageAge.png'>

- 年齢が生存率に与える影響が大きい傾向があるため、
   - Master = 1
   - Miss = 2
   - Mr = 3
   - Mrs = 4<br>

  に変換し、新しい特徴量として使えるようにしておく。

```
data/datasets_nb001
├── nb001_train.csv
└── nb001_test.csv
```

### 20230923
- nb002
  - データの前処理、LightGBM を用いて学習および生存予測
  - One-Hot Encoding で "Sex" と "Embarked" を前処理 (Pandas の get_dummies)
  - LightGBM の導入
    - LightGBMの仕様が変わっているようなので注意 [(参考リンク)](https://qiita.com/c60evaporator/items/2b7a2820d575e212bcf4)
    - score 82.37
    ```bash
    # Early stopping, best iteration is:
    # [29]	training's binary_logloss: 0.301373	valid_1's binary_logloss: 0.400278
    ```

- nb003
  - scikit-learn interface を使用して推定する手法にトライ
  - nb002 と同じ結果が出る事を確認
    - score 82.37
    ```bash
    # Early stopping, best iteration is:
    # [29]	training's binary_logloss: 0.301373	valid_1's binary_logloss: 0.400278
    ```

- nb004
  - ここからオリジナル
  - RandomForestClassifier による推定
  - 話を簡単にするため、object型の列データを除外
  - train_size=0.8, test_size=0.2 で分割（交差検証CV : 無し）<br><br>
    - Case-1 : そのまま推定。random_state=1
    - Validation MAE:  0.238, モデルのスコア:  0.945
    - Kaggle Public Score: 0.72727<br><br>
    - Case-2 : 決定木のmax_leaf_nodesを範囲設定して最小MAEを探索。random_state=1
    - 範囲設定 => range(2,102,1) => 最適ツリーサイズ:  5
    - Validation MAE:  0.182, モデルのスコア:  0.818
    - Kaggle Public Score: 0.78468<br><br>
  - 一般的に Case-2 の方が良いスコアが出るものだが、今回のケースはスコアは却って悪化した
  - もしくは逆に、Case-1 は過学習気味？
  - 両ケースの結果を提出。Public Score は Case-2 の方が良かった<br>
  <img src='.\data\images\readme\nb004_public_score.png' width='800'>
  - 次は交差検証を用いて推定を行う

### 20230924
- nb005
  - RandomForestClassifier による推定に、交差検証を導入
  - 話を簡単にするため、object型の列データを除外
  - 5 fold による交差検証
  - 結果、ツリーの数 n_estimators = 300 が最適と出た<br>
  <img src='.\data\images\readme\nb005_graph_mae_nesti.png'>

  - 各 n_estimators での Average MAE Score<br>
  <img src='.\data\images\readme\nb005_nesti_detail.png'><br>

  - 結果を提出
    - Kaggle Public Score: 0.73684
  - 次の方針はどうするか

### 20231001
- nb006
  - 『探索的データ探索』の本のプロセスを実施。以下メモ。
  - 良いデータを見つけるためのプロセス
    - STEP 1: データの理解
      - まずはコンペの目的、データの概要、意味、値を確認する
    - STEP 2: データのクリーニング
      - データセットには欠損や分析に不適なデータが必ず含まれるため除外
      - 代表的な手法は以下<br>
    <img src='.\data\images\readme\nb006_1.png' width='600'><br>
    - STEP 3: データ分析の切り口の検討
      - どんな切り口で分析するかが非常に重要
      - 代表的な切り口は以下<br>
    <img src='.\data\images\readme\nb006_2.png' width='600'><br>
    - STEP 4: データの分析
      - データの切り口を決めたら、データの分析へ
      - 代表的な分析手法は以下<br>
    <img src='.\data\images\readme\nb006_3.png' width='600'><br>
    - STEP 5: データの選択
      - 分析が終わったら結果をまとめて、目的変数に関連度合いに応じて優先度を付ける

  - データの種類から分析する視点を変える
  - 基本の2パターンは以下
    - 質的データ（カテゴリデータ）
      - 数値で測定できないデータ
    - 量的データ
      - 数値測定が可能なデータ
      - 連続データと離散データの2種類に分かれる
  - 尺度分類　データの分類・水準
    - 以下の4つに分類<br>
    <img src='.\data\images\readme\nb006_4.png' width='800'><br>

  - 欠損値は残すか消すこと、原則として補間処理はしない
    - 探索的データ分析の段階では、欠損値の補間は行わないこと
      - 欠損値が多い場合、または目的変数との関連が弱い場合: データ列を削除する
      - 欠損値が少ない場合、または目的変数との関連が強い場合: 欠損値のまま残す

  - 外れ値は外すこと
    - 外れ値の判断はデータの特性にもよるが、まずは
      - 常識的に考えて異常なデータは除外
      - 範囲による外れ値の判定
        - 例えば上位下位25%（四分位範囲）は除外する<br>
        <img src='.\data\images\readme\nb006_Age_boxplot.png' width='400'><br>
        - 他には、閾値設定を行う<br>
        <img src='.\data\images\readme\nb006_Fare_histplot.png' width='500'><br>
        - 平均32,標準偏差49,最大値512と分布に偏りがある<br>
        <img src='.\data\images\readme\nb006_Fare_detail.png'><br>
        - 運賃50以上は除外した後<br>
        <img src='.\data\images\readme\nb006_Fare_histplot_after.png' width='500'><br>
        - 平均15,標準偏差10と分布の偏りが是正された<br>
        <img src='.\data\images\readme\nb006_Fare_detail_after.png'>

  - データ分析に適した姿へ変換
    - データの型変換（テキストから数値へ変換）
      - 男性/女性　⇒　0/1 に変換
    - データの型変換（数値からテキストへ変換）
      - 数値の範囲から、グループの塊へ変換

  - 規則性を見抜いて意味のあるデータを作成
    - Cabin の先頭文字を見ると、客室ランクを表している事が推察できる<br>
    <img src='.\data\images\readme\nb006_Fare_Cabin_ini.png' width='500'><br>
    - しかし、データのばらつきが多いので利用は難しいか<br>
    <img src='.\data\images\readme\nb006_Fare_Cabin_ini_detail.png'><br>
    - 分析する意味のないデータは、見るだけ時間の無駄なので思い切って削除するのが吉

  - データ分析の切り口6種
    - 要約統計量<br>
    <img src='.\data\images\readme\nb006_5.png' width='800'><br>
    - スライシング
    - ドリルダウン
    - 合成
    - 尺度変換
    - 無名数化

  - データ分析の基本6パターン
    - 単変数のデータ分析
      - 性別で傾向が異なることが分かる<br>
    <img src='.\data\images\readme\nb006_Sex_Age.png' width='500'><br>
    - 変数間のデータ分析
      - 客室ごと年齢を棒グラフで表現
    - 箱ひげ図
      - データの分布が分かる
    - 折れ線グラフ
      - 時系列データ
    - 相関分析
      - 散布図でデータ関係の詳細が分かる
    - ヒートマップ
      - 散布図と同様に関係が分かる
