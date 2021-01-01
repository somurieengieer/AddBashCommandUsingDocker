# Purpose

ローカル端末を汚したくない場合にコマンドをインストールしたDockerコンテナを作成する

# Usage

## ビルドと実行方法

ビルド

```
$ docker build -t imageName .

```

Dockerを実行してcowsayを実行
```
$ docker run -it cow /bin/bash
$ cowsay "I'm cow"
```

## コマンドを作成する

Dockerのコマンドとして実行
```
$ docker run -it --rm  cow hello
```

### コマンド実行用のファイルを作成する

以下のような内容で「cowsay」ファイルを作る
```
#!/bin/sh
if [ $# -ne 1 ]; then
  echo "cowboy command need 1 argment"
  exit 1
fi
docker run -it --rm cow $1
```


作成したcowsayをaliasに登録する。以下はcallmeでcowsayが呼ばれるようになる例。
```
$ alias callme='/〜〜/cowsay'  # aliasの設定
$ callme hello                 # 実行方法の例
```

※aliasの一覧は以下の通り
```
$ alias      # alias一覧を表示する
$ alias -p   # alias一覧を表示する。こちらでも同じ結果が出る
$ unalias [command] # aliasを削除
```

### aliasの別の方法(ボツ)

もしくは/usr/local/bin/に設定でもOK。/usr/local/bin汚れるの嫌だから微妙かも。

```
$ ln -s cowsay /usr/local/bin/cowsay
```

## コマンドを永続的に使用する

高頻度で使うようなコマンドは~/.bash_profileに以下のように登録する。(bashの場合)

```
$ alias callme='/〜〜/cowsay'  # aliasの設定
```