- レジストリ(DockerHub)
    - リポジトリ
        - イメージA
            - タグA
            - タグB
        - イメージB
            - タグA
            - タグB

イメージをローカルに持ってくる  
`$docker pull REPOSITORY:TAG`

所有しているイメージ一覧  
`$docker imaegs`

イメージからコンテナの起動  
`$docker run REPOSITORY:TAG`

実行中のコンテナ一覧  
`$docker ps`

コンテナ一覧  
`$docker ps -all`

イメージからコンテナのターミナルに接続  
`$docker run -it ubuntu:latest bash`

ターミナルに接続中にコンテナを停止せずに抜ける  
`ctrl+p+q`

エラーで終了したコンテナ一覧を表示  
`$docker ps -a --filter "exited=1"`

コンテナ内で追加プロセスを実行    
`$docker exec -it CONTAINERID bash`

ログ表示  
`$docker logs CONTAINERID`

すべてのコンテナを削除  
`$docker rm $(docker ps -aq)`

コンテナと元イメージの変更点を表示  
`$docker diff <CONTAINERNAME>`

コンテナの変更点を記録し新しいコンテナを作る  
`$docker commit <CONTAINERID> <USERNAME/APPLICATION:TAG>`

Dockerfileからイメージを構築する  
`$docker build -tag <TAGNAME> <PATH>`  

イメージの履歴を表示する  
`$docker history <IMAGE>`  

エントリポイントの上書き(例：bashを実行する)  
`$docker run --entrypoint bash -it <IMAGE>`  

Dockerfileの主な命令
```
FROM(イメージ)
MAINTENER(誰がDockerfileを書いたか記述)
RUN(ビルド時に実行するコマンド)
CMD(コンテナ起動時に実行するコマンド,優先順位はコンテナ起動時の引数＞CMD命令)
ENTRYPOINT(runコマンド実行時に設定したエントリポイントの引数を受け付ける)
COPY(特定の送信元から、特定の送信先コンテナ・ファイルシステム上にファイルやディレクトリをコピーする)
WORKDIR(指定されたディレクトリで命令を実行する)
ENV(環境変数を設定する)
ADD(ファイルやディレクトリをソースからコピーして作る)
```

Dockerfileベストプラクティス
- Dockerfileの各行が新しい層を作る
- イメージ構築にたくさんの層を使用するため、Dockerfileの読みやすさとの間に、適切なバランスが必要
- 不要なパッケージはインストールしない
- DockerfileごとにENTRYPOINTは一つだけ(One ENTRYPOINT per Dockerfile)
- 同じコマンドを一つにまとめ、かつ可読性を上げるため、&&や\を使用する
- キャッシュシステム
    - 命令の順番を考慮する
    - 最初に変更の少ないファイルの追加をおこない、大きな変更を伴うものは最後に追加

