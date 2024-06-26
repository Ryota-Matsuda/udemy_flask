# udemy_flask
udemyで、flaskを学習した際に作成したものを格納するリポジトリ

# sshでのGitHubへのアクセス手順
[こちらの記事](https://qiita.com/suthio/items/2760e4cff0e185fe2db9)を参照
1. 事前準備
Unixコマンドを使用できる環境を開く(コマンドプロンプトor powershellを管理者権限で実行)
2.  新しいSSH Keyの作成
~~~
ssh-keygen -t ed25519 -C "your_email@example.com"
~~~
以下のようにSSHの保存先を聞かれるが、気にしない場合は気にしなくてOK
~~~
Enter file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
~~~

以下のようにパスフレーズの入力を求められるが、こちらも特に記入しなくてもOK
~~~
Enter file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
~~~

3. ~/.ssh/id_rsa.pubの内容をクリップボードにコピーする

4. SSH Keyを登録する
    1. GitHubにログインし、右上のプロフィールをクリックする
    2. Settingsで設定画面に遷移
    3. 左のメニューから'SSH Key'を選択
    4. 'Add SSH Key'をクリック
    5. Bodyにコピーしたid_rsa.pubの内容をペースト
    6. 'Add Key'をクリック

5. 確認
ターミナルで以下を入力
~~~
ssh -T git@github.com
~~~

以下のような表示が出れば成功
~~~
Hi Ryota-Matsuda! You've successfully authenticated, but GitHub does not provide shell access.
~~~

# PythonとFlaskの環境構築
1. Pythonのインストール
2. 仮想環境の構築
仮想環境を構築したいディレクトリに移動後、以下のコマンドを実行し、仮想環境を構築する
仮想環境を構築する理由は、使用するアプリケーションに応じて、Flaskのバージョンを管理したい場合があるから
~~~
mkdir myproject
cd myproject
py -3 -m venv venv
~~~
3. 仮想環境でFlaskのインストール
以下のコマンドを実行し、仮想環境を有効にする
~~~
./venv/Scripts/activate
~~~
カレントディレクトリの表示が以下のようになれば成功
~~~
(venv) PS C:/…/…/…
~~~

以下のコマンドを実行し、Flaskをインストールする
~~~
pip install Flask
~~~

4. 確認
~~~
flask --version
~~~
上記のコマンドを実行し、

~~~
Python 3.12.3
Flassk 3.0.3
Werkzeug 3.0.3
~~~
のように、flaskのバージョンが表示されれば成功。

# Flaskの実行方法
1. 仮想環境をactivateする
PowerShellやコマンドプロンプトを起動後、myprojectディレクトリに移動し、以下のコマンドを実行する
~~~
./venv/Script/activate
~~~

ディレクトリの表示が、以下のように左端に(venv)が表示されれば成功
~~~
(venv) PS C:\Users\ryota matsuda\Desktop\udemy_study\udemy_flask\myproject>
~~~

2. 環境変数の設定
以下2つの環境変数を設定する
~~~
$env:FLASK_APP = "app"
$env:FLASK_ENV = "development"
~~~

3. Flaskの実行
以下のコマンドを実行する
~~~
flask run
~~~

デバッグモードで起動するときは、以下のコマンドを実行する
~~~
flask run --debug
~~~