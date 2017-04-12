### StateとProps

State (状態)
- mutable data (可変のデータ)
- maintained by component (コンポーネントによって保持)
- can change it (変更可)
- should be considered private (プライベートであるべき)

具体例  
- ドロップダウンが閉じているか（UIに関連した状態）  
- 現在ログインしているユーザの名前（外部のデータに関連する状態）  


Props (プロパティ)

- immutable data (不変のデータ)
- passed in from parent (親から渡される)
- can't change it (変更不可)
- can be defaulted & validated (デフォルト値の設定と検証が可能)


### コンポーネント
- コンポーネントは親子関係
- 自ら変更可能なプロパティであるstateを持つのは親コンポーネント、この状態は親から子にpropsを渡して管理する
- イベントもpropsとして子に渡す

### stateless functional components
propsを受け取り、何をレンダリングすべきかを返す関数を、React.Componentを継承するクラスを定義するよりもシンプルに書いたもの
```jsx
function Square(props) {
  return (
    <button className="square" onClick={() => props.onClick()}>
      {props.value}
    </button>
  );
}
```
