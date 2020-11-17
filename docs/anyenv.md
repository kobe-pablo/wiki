# anyenv
https://github.com/anyenv/anyenv

## anyenvとは
anyenvとは、実行環境のバージョンを管理するツール郡を、一元管理するツールである。

### いいところ
**envのいいところ
- プロジェクトごとに処理系のバージョンを切り替えることが出来る。
- 使用しているバージョンの情報をコード管理出来る。

anyenvのいいところ
- 言語のインストールが簡単
- パスをanyenvに通すだけで良い(**envをたくさん導入していくとパスが通らない問題が発生するらしい)
- **envをまとめて管理できる

## anyenv導入後のツール群のイメージ
```
homebrew
├── anyenv
│   ├── pyenv
│   │   ├── python 3.8.3
│   │   ├── python 3.7.8
│   │   └── python 2.7.18
│   ├── nodenv
│   │   ├── node 14.2.0
│   │   └── node 11.15.0
│   ├── rbenv
...
```

## インストール
PCに直接インストールしているpythonやnodeはがんばって削除すると良い。  
すでに`pyenv`や`nodenv/nodeenv/ndenv/nodebrew`や`rbenv`など入れてる場合それらも削除すると良い。

```bash
# Homebrewにインストール
$ brew install anyenv
# セットアップ
$ anyenv init
```
その後、以下のようなメッセージが出るので内容に従って `eval "$(anyenv init -)"`を書き足すなどする。

```bash
# 実行環境に応じて出力が変わるので要注意

# Load anyenv automatically by adding
# the following to ~/.zshrc:
eval "$(anyenv init -)"
```

ターミナルを開き直すと、以下のようなメッセージが出るので、メッセージに従って初期セットアップを実施。

```
ANYENV_DEFINITION_ROOT(/Users/riywo/.config/anyenv/anyenv-install) doesn't exist. You can initialize it by:
> anyenv install --init
```
```bash
# 必要に応じて以下を実行
$ anyenv install --init
```

### anyenv-update
`anyenv update`コマンドでanyenv内の**env全てをアップデートしてくれるプラグイン。以下のコマンドを実行しインストールする。
```bash
$ mkdir -p ~/.anyenv/plugins
$ git clone https://github.com/znz/anyenv-update.git ~/.anyenv/plugins/anyenv-update
```

## 使い方
```bash
# **envのインストール
$ anyenv install rbenv
$ anyenv install pyenv
$ anyenv install nodenv
$ exec $SHELL -l  # シェルの再起動/再ログイン

# あとはそれぞれの**envを利用する
$ rbenv install ...
$ pyenv install ...
$ nodenv install ...
```

```bash
# 何がインストールされてるかを一括で確認
$ anyenv versions
nodenv:
* 12.16.3 (set by /Users/xxxxx/.anyenv/envs/nodenv/version)
  14.0.0
pyenv:
  system
  3.6.11
* 3.8.3 (set by /Users/xxxxx/.anyenv/envs/pyenv/version)
```

## **envの使い方
1. `$ **env install xx.xx.xx`で使用するバージョンを**envにインストール
2. `$ **env global(local) xx.xx.xx`を実行して使用するバージョン指定する

### よく使うコマンドの一覧(ex. nodenv)
```bash
# インストール出来るバージョンのリストを表示
$ nodenv install --list

# install a Node version:
$ nodenv install 0.10.0

# ローカル(カレントディレクトリ)に.node-versionを作成。これでバージョンを指定する。
$ nodenv local xx.xx.xx
$ nodenv local --unset  # 設定解除
$ nodenv local  # ローカルで設定されているnodeのバージョン確認

# グローバルで使うバージョンの設定
$ nodenv global xx.xx.xx
$ nodenv global --unset #設定解除
$ nodenv global # グローバルで設定されているnodeのバージョン確認


# *は現在利用中のバージョン
$ nodenv versions
  0.8.22
  0.9.12
  * 0.10.0 (set by /Users/xxxxx/.anyenv/envs/nodenv/version)
```
