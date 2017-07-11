### スプレッド演算子(spread operator)

- 配列のコピー
```javascript
let d1 = [1, 2, 3];
let d2 = [...d1];
d2[1] = 10;
console.log('d1:', d1); // => [1, 2, 3] # 影響を受けない

//ES5
let d2 = d1.slice();
```

- 配列の展開
```javascript
let d1 = [1, 2, 3];
let d2 = [0, ...d1, 4, 5];
console.log(d2); // => [ 0, 1, 2, 3, 4, 5 ]
```

- 関数の呼び出しに対して
```javascript
function func1(a, b, c) {
    console.log('func1', a, b, c);
}
let d = [1, 2, 3];
func1(...d); // => func1 1 2 3

//ES5
func1.apply(null, d);
```

- 直接変更を伴うデータの変更と直接変更を伴わないデータの変更
```javascript
var player1 = {score:  1};
var tmp1 = {};
tmp1 = player1;
player1.score = 2;// same object mutated {score: 2}
console.log(tmp1);
//Object { score : 2 }
var player2 = {score: 1}
var tmp2 = {};
tmp2 = player2;
player2 = {...player2, score: 2}// new object not mutated {score: 2}
console.log(tmp2)
//Object { score : 1 }
```
- if
```javascript
if(Object){
  console.log('true');
}else{
  console.log('false');
}
//true
if(String){
  console.log('true');
}else{
  console.log('false');
}
//true
if(Number){
  console.log('true');
}else{
  console.log('false');
}
//true
if(0){
  console.log('true');
}else{
  console.log('false');
}
//false
if(null){
  console.log('true');
}else{
  console.log('false');
}
//false
if(undefined){
  console.log('true');
}else{
  console.log('false');
}
//false

```

### tips
- オブジェクトの配列の中から要素を探す
```javascript
ObjectsArray.find(element => element.keyValue === 'hoge')
```

- プロパティが存在するかどうか判定する
```javascript
//プロパティが文字列で、0文字のときもtrueになる
if('hoge' in fuga){}
```
