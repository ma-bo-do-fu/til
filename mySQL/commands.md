- アクセスする  
`$mysql --host=X.X.X.X --user=XXX`  
- DB一覧を表示する  
`> show databases;`  
- DBにアクセスする  
`>use <DBNAME>;`  
- テーブル一覧を表示  
`>show tables (from <DB_NAME>);`  
- カラム一覧を表示  
`>show columns from <TABLE_NAME>;`  
- 予約語をカラムとして使う場合はバックスラッシュでエスケープする  
``>select `<COLUMNNAME>` from <TABLE_NAME>;``  