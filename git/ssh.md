# gitのリモートディレクトリにSSH鍵を登録する

`$cd ~/.ssh`  
- 鍵を生成する  
`$ssh-keygen -t rsa`  
- 鍵を登録する  
`$pbcopy < ~/.ssh/YOUR_PUBLICKEY_PATH`  

- ssh/configを設定する
```
Host HOST_NAME
  HostName HOST_NAME
  IdentityFile ~/.ssh/SECRET_KEY_PATH
  User git
```  
例  
```
Host github.com
  HostName github.com
  IdentityFile ~/.ssh/SECRET_KEY_PATH
  User git
```
