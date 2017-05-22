- Ubuntuのbuld-essentialsをCentOSでやりたい  
Ubuntu  
`$apt-get install build-essentials`   
CentOS  
`$yum groupinstall "Development Tools"`　  
`$yum install kernel-devel kernel-headers`  

- bashで単語移動  
http://qiita.com/odacoh/items/b94be0deecaaa27b0263

- 自動起動のコマンド  
chkconfig

- CentOSでのipconfig  
`$ip addr show`

- bash_profileの再読込  
`$source .bash_profile`

- sshの接続確認  
`$ssh -vT <IPAddress/HostName>`  

- コマンドの履歴を表示する  
`$history`  

- シェルスクリプトのファイルを作成し実行する  
`$touch hoge.sh`  
`$chmod +x hoge.sh`  
`$./hoge.sh`  

```bash
#!/bin/sh
#変数
hoge=$((RANDOM % 2))
#if文
if [ $hoge = 0 ] ; then
  echo "hoge"
else
  echo "huga"
fi
#直前のコマンドのステータス
echo $?
#ループ
for i in `seq 0 9`
do
  #コマンド実行
  ls
done
```

