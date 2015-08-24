class: center middle
# es6 と Functional Programing

2015/8/24

---
class: middle

## 自己紹介

- Takezawa Toshiki
- [@to4iki](https://twitter.com/to4iki)
- 広く浅く

---
# ECMAScript 6!!!
- New Syntax
- New Global Objects
- Improvements of Existing Classes

---
## 少し触ってみて
- 普通のclass, 普通のscope
- モダンなsyntax, 関数型に寄った拡張
- 直ぐに動かせる(used babel)
- 未だ手のかかる部分もあってかわいい

---
## New Syntax
- class
- Module
- Arrow Function =>
- Generator
- etc...

---
## class

```javascript
class User {
    constructor(name) {
        this.name = name;
    }

    say() {
        return `name is (${this.name})`;
    }

    static apply(name) {
        return new User(name);
    }
}
```

```javascript
class Admin extends User {
    toString() {
        return '[Admin] ' + super.toString();
    }
}
```

---
## Arrow Function

```javascript
var fute = {
    name: 'futeshi',
    delayHello: function() {
        // var self = this;
        // 無名関数の内部ではthisはGlobal Objectを指す
        setTimeout(function() { console.log('hello ' + this.name); }, 1000);
    }
}
fute.delayHello() // hello
```

↓ toES6

```javascript
const fute = {
    name: 'futeshi',
    delayHello: function() {
        setTimeout(() => console.log('hello ' + this.name), 1000);
    }
}
fute.delayHello() // hello futeshi
```

---
## New Global Objects
- Promise
- Map/Set
- etc...

---
## Improvements of Existing Classes
- Object
- String
- etc...

---
class: center middle

# Functional Programing

---
## 関数型プログラミングとは
- データ型の定義を行い、そこに関数の定義を加えていくスタイル
- プログラム中で動的に変化する状態をオブジェクトや構造体、変数の粒度で管理されるとき、その状態は「明示的状態」と呼ばれ、プログラム中で変数間の関係性が宣言的に記述され、イミュータブル性が維持される状態を「暗黙的状態」または「宣言的状態」という。このパラダイムを採用しているプログラミングスタイルのことを関数型プログラミングと呼ぶ

---
### うま味
- 状態を持たないようにするので、コードを追いやすい
- 関数型言語で書かれたコード(参照透明な言語)は並列化しやすい
    - 関数全てが参照透明な言語なら例.g()はf()の結果に依存しないなら、いつでも並列化可能
- 関数の評価結果がコンテキストに依存しないため、テストがしやすい

---
## シンプルに
副作用を排除し関数オブジェクトを駆使するプログラミング

1. 変数は再代入禁止である(定数)
2. 関数は参照透過性が保たれている(副作用がない)
3. 関数が第一級オブジェクト(関数を値として扱える)
4. パターンマッチ
5. 再帰により繰り返し構造

---
### 1. 変更不可能な変数宣言

再代入不可の変数を宣言

```javascript
const name = 'takezawa';
name = 'hoge'; // "name" is read-only
```

---
### 2. 副作用無し

```javascript
function double1(nx) {
    for(var i = 0; i < nx.length; i++) {
        nx[i] = nx[i] * 2;
    }
    return nx;
}

let nx = [1,2,3]
p(double1(nx)) // [2,4,6]
p(double1(nx)) // [4,8,12]
```

↓

```javascript
function double2(nx) {
    return nx.map(x => x * 2);  
}

let nx = [1,2,3]
p(double2(nx)) // [2,4,6]
p(double2(nx)) // [2,4,6]
```

---
### 2. 副作用無し

```javascript
var ary = [0,1,2,3,4,5,6,7,8,9], r = [];
for (var i=0; i<=ary.length; i++) {
    if (ary[i] % 2 == 0) {
        r.push(ary[i] * ary[i]);
    }
}
// [0,4,16,36,64]
```

↓

```javascript
[...Array(10).keys()].filter(x => x % 2 == 0).map(x => x * x);
// [0,4,16,36,64]
```

---
### 3. 高階関数

関数を値として扱う事が出来る

- 引数に関数を渡して処理を委譲

```javascript
const calc = f => f(3,2);
const add = (...xs) => xs.reduce((a,b) => a + b);
const multi = (...xs) => xs.reduce((a, b) => a * b);

calc(add) // 5
calc(multi); // 6
```

---
### 3. 高階関数

- 関数を返り値として処理を委譲
    - クロージャーによる返り値として関数を返す

```javascript
// currying
const curry2 = f => a => b => f(a, b);
const plus = (x, y) => x + y;

const curriedOnePlus = curry2(plus)(1)

curriedOnePlus(2) // 3
curriedOnePlus(3) // 4
```

---
### 4. パターンマッチ
- パターンマッチにより値の取出を行う
- パターンマッチにより代入などの副作用を減らす事が出来る

分割代入(destructuring)

```javascript
// 可変長引数の活用
const [head, ...tail] = [1,2,3] // head: 1, tail: [2,3]

// objectからの抽出
const { foo: { bar: [,x] } } = { foo: { bar: [1,2,3] } } // x: 3
```

---
### 5. 末尾呼出し最適化
- 再帰の方が代入などの副作用がなく、短く書ける場合がある
- 末尾呼出し最適化により再帰でのスタックオーバーフローを回避

```javascript
function factorial1(n) {
    let r = 1, i = 1;
    for (i; i<=n, i++) { r *= i; }
    return r;
}

function factorial2(n, acc) {
    return (n == 0) acc : factorial(n-1, n*acc);
}

factorial2(100000); // doesn't cause stack overflow
```

---
### 無限リスト

無限の旅

```javascript
function* Stream() {
    let i = 0;
    while (true) yield i++;
}
```

```javascript
const g = Stream();
g.next().value; // 0
g.next().value; // 1
g.next().value; // 2
g.next().value; // 3
// ...

for (let v of g) {
    // ∞
}
```

---
## まとめ

- ES6使おう
    - [Babel · The compiler for writing next generation JavaScript](https://babeljs.io/)
- 関数型のパラダイムに乗っ取った書き方ができる
- 宇宙は無限だ

---
## see also
- [Run through ES6](https://teppeis.github.io/run-through-es6)
- [Effective ES6](http://www.slideshare.net/teppeis/effective-es6)
- [ES6時代のJavaScript - クックパッド開発者ブログ](http://techlife.cookpad.com/entry/2015/02/02/094607)
- ES6で書いた自作Library
    - [to4iki/prefn](https://github.com/to4iki/prefn)
    - [to4iki/data.monad](https://github.com/to4iki/data.monad)
