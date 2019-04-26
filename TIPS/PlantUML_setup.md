# PlantUMLのセットアップ

## PlantUMLとは

PlantUML は、以下のような図をテキストで素早く描くためのオープンソースプロジェクトです。

- シーケンス図
= ユースケース図
- クラス図
- アクティビティ図
- コンポーネント図
- 状態遷移図
- オブジェクト図

## 環境

下記の環境で動作確認しました。

- Windows 10 Pro (64bit)
- [Visual Studio Code 1.33.1](https://code.visualstudio.com/)
- [Java SE Runtime Environment 8 Update 211](https://www.java.com/ja/download/)
- [Graphviz 2.38](https://graphviz.gitlab.io/_pages/Download/Download_windows.html)
- [PlantUML 2.10.9](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)

## セットアップ

### Visual Studio Codeのインストール

1. 上記のリンクを開く
2. [Download for Windows] を押してインストーラーをダウンロードする
3. ダウンロードしたインストーラーを実行する

### PlantUMLのセットアップ

1. Javaのインストール
   
   PlantUMLの実行には、Javaの実行環境が必要となります。
   
   1. 上記のリンクを開く
   2. [無料Javaのダウンロード]ボタンを押す
   3. [同意して無料ダウンロードを開始]を押し、インストーラーをダウンロードする
   4. ダウンロードしたインストーラーを実行する

2. Graphvizのインストール
   PlantUMLがUMLを描画するために使用しているソフトウェアです。

   1. 上記リンクを開く
   2. [graphviz-2.38.msi]を選択してインストーラーをダウンロードする
   3. ダウンロードしたインストーラーを実行する
   
3. PlantUMLのインストール
   
   Visual Studio MarketplaceでPlantUMLをインストールします。

   1. Visual Studio Codeを起動する
   2. ”**Ctrl** + P"と入力して、Quick Openを開く
   3. Quick Open に **ext install plantuml** と入力して、Enter キーを押す 
   4. 検索結果から**PlantUML**を選択し、[インストール]を押す
   5. インストール完了後にVisual Studio Codeを再起動する

### 動作確認

1. プレビュー表示
   
   1. Visual Studio Codeを起動する
   2. 拡張子.**pu**で新規ファイルを作成する
   3. ファイルに以下を入力し、”**ALT + D**"でプレビューを表示する
   
   ```test.pu
   @startuml
   title シーケンス図
   アリス -> ボブ: リクエスト
   ボブ --> アリス: レスポンス
   @enduml
   ```

2. 画像ファイルとして出力
   
   1. "**Ctrl + Shift + P**"でコマンドパレットを開く
   2. **PlantUML:Export Current Diagram**と入力する
   3. **png, svg, eps, pdf, vdx, xmi, scxml, html**から出力形式を選択する
   
   出力結果のPNGファイルは以下のようになります。

   [画像ファイル](./シーケンス図.png)


### PlantUML言語リファレンス

PlantUMLの文法は、"PlantUML Language Reference Guide"としてPDFファイルが提供されています。

1. [http://plantuml.com/download](http://plantuml.com/download)を開く
2. PlantUML Language Reference Guide にある日本語を選択する
3. "PlantUML_Language_Reference_Guide_JA.pdf"がダウンロードされる