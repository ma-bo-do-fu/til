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

コンテナの起動
`$docker run REPOSITORY:TAG`

実行中のコンテナ一覧
`$docker ps`

コンテナ一覧
`$docker ps -a`

ターミナルに接続
`$docker run -it ubuntu:latest bash`

ターミナルに接続中にコンテナを停止せずに抜ける
`ctrl+p+q`

エラーで終了したコンテナ一覧を表示
`$docker ps -a --filter "exited=1"`

コンテナ内で追加プロセスを実行
`$docker exec -it CONTAINERID bash`

ログ表示
`$docker logs CONTAINERID`
