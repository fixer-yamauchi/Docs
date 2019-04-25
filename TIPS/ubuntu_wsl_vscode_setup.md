# ubuntu、wsl-terminal、Visual Source Code、Github連携までのセットアップ
## ubuntuのセットアップ
- Microsoft StoreからUbuntuをインストールする
- インストール後、Ubuntuを起動し、usernameならびにpasswordを入力する
- SSH Keyを作っておく
- ディレクトリを作成する
```
mkdir ~/.ssh
```
- ディレクトリに移動する
```
cd ~/.ssh
```
- SSH Keyを生成する
```
ssh-keygen -t rsa -b 4096 -C "**<メールアドレス>**"
```
- ホームディレクトリを変更する
- 設定ファイルを変更する
```
sudo vi /etc/passwd
``` 
- 自分のユーザ名の設定行を書き換える
```
**<自分のユーザ名>**:x:1000:1000:,,,:**<ホームディレクトリ>**:/bin/bash
```
## wsl-terminalのセットアップ
- [wsl-terminal](https://github.com/goreliu/wsl-terminal/releases)から最新版をダウンロードする
- ダウンロードしたファイルを解凍し、**C:\Apps\wsl-terminal**などの好きなフォルダに保存する
- **open-wsl.exe**のショートカットを作成し、スタートメニューに追加する
- ショートカットファイルのプロパティを開き、リンク先の末尾に「-l」を追加することで、ターミナルが起動した時にホームディレクトリにいる状態になる
- wsl-terminal起動後、念のため**pwd**コマンドで、ホームディレクトリが変更されているかを確認する
- 「To run a command as administrator (user "root"), use "sudo <command>".」が表示される場合は最初のsudoを行う
```
sudo ls
```
- Linux側のsshのディレクトリをWindows側にシンボリックリンクする
```
ln -s /home/ユーザ名/.ssh ~/
```
## Visual Source Codeのセットアップ
### 起動するTerminalの設定変更
- [**File**] -> [**Preferences**] -> [**Settings**]を選択する
- Search settingsで**terminal.integrated.shell.windows**を検索する
- 起動するTerminalを”**C:\Windows\System32\wsl.exe**”に変更する
### wsl用のgitを設定する
- [wsl用のgit(wslgit.exe)](https://github.com/andy-5/wslgit/releases)をダウンロードする
- ダウンロードした**wslgit.exe**を**C:\Apps\wslgit**などの好きなフォルダに保存する
- [**File**] -> [**Preferences**] -> [**Settings**]を選択する
- Search settingsで**git.path**を検索する
- **Edit in settings.json**のリンクを選択する
- DEFAULT USER SETTINGの「"git.path": null」の行の左にある鉛筆マークを選択し、「Copy to Settings」を選択すると、USER SETTINGSに行が追加される
- 「"git.path": **null**,」を「"git.path": **"C:\\Apps\\wslgit\\wslgit.exe"**,」に変更する
- **settings.json**を保存する
## Githubのセットアップ
### Githubのsettingsで作成したSSH Keyを設定する
- 公開鍵をコピーしてGithubに設定する
```
cat ~/.ssh/id_rsa.pub
```
- Githubに接続できるか確認する
```
ssh -T git@github.com
```
### レポジトリの作成
- [github.com](https://github.com/)にログインする
- 左側「Repositories」の横の[**New**]ボタンを押下する
- 「Repository name」に作成するレポジトリ名を入力する
- 「Description」に説明を入力する
- Public/Privateのいずれかを選択する
- 「Initialize this repository with a README」を選択する
- [Create repository]ボタンを選択する
- [**Clone or download**]ボタンを押下し、URLをコピーする
- ローカルレポジトリとするディレクトりで、gitの初期化を行う
```
git init
```
- ユーザ名を設定する
```
git config --global user.name "**<ユーザ名>**"
```
- Eメールを設定する
```
git config --global user.email **<Eメール>**
```
- リモートリポジトリを追加する
```
git remote add origin **<コピーしたリモートリポジトリのURL>**
```
- 最初のpushを行う
```
git push -u origin master
```
- (Githubとの接続がHTTPS方式の場合）認証情報を保存する
```
git config --global credential.helper cache
```
