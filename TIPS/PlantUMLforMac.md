# PlantUML for Mac

## Visual Studio CodeにExtensionをインストール

ExtensionのPlantUMLをインストール

## Alt + dでPreviewするも、「Javaがいない！」と怒られた。

[Javaのダウンロードサイト](https://www.java.com/en/download/mac_download.jsp)からJavaをダウンロードしてインストール

## graphvizインストールしてなかった

インターネットで調べたら、graphvizが必要だったのを忘れていた

```
brew install graphviz
```

## Javaのbinのpathを通せと怒られる

もう一度、Alt + dでPreviewを試すも、まだPreviewされない。<br>
エラーが出ているのでみてみると、Javaのbinのpathが通っていないと怒られている。<br>
ホームディレクトリに.bash_profileを作成してpathを通す。<br>
```
touch .bash_profile
```
javaのbinのディレクトリを探して、.bash_profileに以下を追記する。
```
export PATH=$PATH:/Library/"Internet Plug-Ins"/JavaAppletPlugin.plugin/Contents/Home/bin
export JAVA_HOME=/Library/"Internet Plug-Ins"/JavaAppletPlugin.plugin/Contents/Home
```
.bash_profileを適用する
```
source ~/.bash_profile
```
ターミナルを再起動して、、もう一度、Alt + dでPreviewを試すとちゃんとPreviewしてくれました。


