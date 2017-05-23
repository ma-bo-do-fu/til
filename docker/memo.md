### レジストリとリポジトリのイメージ

- レジストリ(DockerHub)
    - リポジトリ
        - イメージA
            - タグA
            - タグB
        - イメージB
            - タグA
            - タグB

### コマンドtips

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
`$docker run --interactive --tty ubuntu:latest bash`

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

エントリポイントの上書き(例：bashを実行する)  
`$docker run --entrypoint bash -it <IMAGE>`  

イメージにタグ付けする  
`$docker tag <IMAGENAMEorID>:<TAG> <NEWNAME>:<TAG>`  

DockerHubアカウントにログインする  
`$docker login`  

DockerHubにイメージをアップロードする  
`$docker push <IMAGENAME:TAG>`  
  
コンテナにボリュームをマウントする  
`$docker run --detach --volume <PathToVolume> <IMAGENAME>` 

コンテナにホストマシンのディレクトリをマウントする  
`$docker run -v <HostDirectory>:<ContainerDirectory> <IMAGENAME>` 

コンテナの情報を確認する  
`$docker inspect --format=='{{.KEY1.KEY2}}' <CONTAINERID>`  

ボリューム一覧を表示する  
`$docker volume ls`  

ボリュームを削除する  
`$docker volume rm <VOLUMENAME>`  

ポートを割り当ててコンテナを実行  
`$docker run -p <HostPort>:<ContainerPort> ubuntu bash`  

コンテナの名前を指定して実行  
`$docker run --name mynginx nginx`  

データボリュームを利用する  
`$docker run -it --volumes-from <DATACONTAINER> <IMAGENAME:TAG>`  

複数のデータボリュームを利用する  
```
$docker run -it --volumes-from <DATACONTAINER1> \
 --volumes-from <DATACONTAINER2> <IMAGENAME:TAG>
 ```

ログデータのバックアップをおこなう 
``` 
$docker run --volumes-from <DATACONTAINER> -v <Path/To/Host>:<Path/To/Container> <IMAGENAME:TAG> \
 tar cvf <Path/To/Host(Logfile.tar)> <Path/To/Container(LogfileDirectory)>
```
ポートの割当を確認する  
`$docker port <CONTAINERID>`  

コンテナ間を連携する  
`$docker run -d -it --name <CONTAINER1> --link <CONTAINER2>:<ALIAS> <IMAGE> bash`  

### DataVolumeとDataVolumeContainer
Data Volume とは「複数のコンテナ間で永続的なデータや共有データを扱うために Union File System を無視する特別なディレクトリ」のこと  
複数のコンテナ間で共有したい永続的なデータや非永続的なコンテナから参照したい永続的なデータは Data Volume Container と呼ばれるコンテナを作成して、そのコンテナからデータをマウントする  

### Dockerfiletips

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
VOLUME(<PATH/TO/CONTAINER>パスを指定してボリュームをマウントする)
EXPOSE(<CONTAINERPORT> <HOSTPORT>公開するポートを指定する)
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

alphine linuxのターミナルに入る  
`$docker exec -it <CONTAINERID> /bin/sh`    
