
- 差分を確認しながらステージングする  
`$git add -p`  

- リモートブランチを削除する  
`$git push --delete origin <branch_name>`  


- リモートブランチをローカルにチェックアウトする  
`$git checkout -b <local_branch> origin/<remote_branch>`  

- リモートブランチのコミットを2つ分削除する  
`$git push -f origin HEAD^^:master`  
