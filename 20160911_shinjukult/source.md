class: center middle

## やりたい事
Shinjuku.LT 第1回 2016/9/11

???
- http://qiita.com/harasou/items/1fa3cca6ac1ef175c876
- https://github.com/gnab/remark/wiki/Markdown#slide-notes

---
class: middle center

## 自己紹介
- Takezawa Toshiki
- [@to4iki](https://twitter.com/to4iki)

---
class: middle center

## GANMA!
- Web
    - [GANMA!(ガンマ)](http://ganma.jp/)
    - [つぶやきGANMA!](http://tsubu.ganma.jp/)
- iOS
- Android
---
class: middle center

## 最近やったこと、やっていること

---
class: middle center

- リファクタリング
- パフォーマンスチューニング
- UITests(結合テスト)の導入
- CIの調整
- 広告SDK導入、計測SDK周りの調整@iOS/Android
- アプリ初回起動時のチュートリアルの実装@iOS
- UniversalLinksの導入@iOS
- iOS10対応
- 新人さんの教育関連のお手伝い
- etc...

---
class: middle center

### 最近はいわゆる防御的なタスクをやっている

---
class: middle center

### なので、今日は今後やりたいことを話す

---
class: middle center

# やりたいこと

???
の前に、少し考えて見たい教訓があります。  

---
class: middle center

# 手段と目的をはき違えるな

???
有名な言葉がありますよね。目的・手段論    
これを実現するため(目的)にこの手段を用いる。  
- 技術を用いることが第一に来てはいけない
- あくまでも目的を重視して仕事などのプロジェクトを遂行するべきというフレーズとして使われているように思います
- 先のJava7 > 8 への移行、docker

---
class: middle center

### If all you have is a hammer, Everything looks like a nail
[ハンマーしか持っていなければすべてが釘のように見える](https://burnworks.com/news/article/159/)

???
ある手段に固執してしまうことによって、問題の本質を見失ったり、本来するべきでない事をする、あるいはするべき事ができなくなるという現象が、Web サイトの制作や運営、その改善プロセスにおいても起こることが珍しくないからです。

- A/B テストやデータを基にすること自体に問題はありませんし、うまく活用すればよい結果をもたらすものですが、データのみに目が行きすぎるのは危険と言わざるを得ません。
- デザインパターン: 不適切な場所に原則を適用し、存在しないところにパターンを見出す。

---
class: middle center

# 正直モヤっとする

???
減らず口というか、いい風に解釈しているだけかもしれないが、
- 目的と手段というのはスコープによって異なってくるのでは?
- 文脈に依存しているのでは?

---
class: middle center

### 俯瞰してみれば、僕たちがやっていることは全て手段なのでは?
![](http://cdn-ak.f.st-hatena.com/images/fotolife/h/h13i32maru/20141227/20141227222421.png)

???
この目的を達成するための手段にすぎない
- 顧客第一を達成するため(目的)、技術(手段)を使う」切り口を変えると「会社の利益を上げるため(目的)、顧客第一(手段)を用いる」や「ある技術を導入するため(目的)、上司を説得する(手段)」などにもなります。つまりある切り口では目的だったものが別の切り口では手段になるのです。

---
class: middle center

### 例えば、
- 大学受験に合格するという目的 == 大学に入学することが今後の自分の可能性を広げるための手段にすぎない
- KPIの達成という目的 == 利益を上げるための手段
- 会社の存在そのもの == 営利をなすための手段

???
僕たちプログラマは手段のスペシャリストになるべき

---
class: middle center

## プログラマは手段のスペシャリスト

???
- ある分野に精通してそれを手段として使いこなせるようになるためにはそれなりの時間と経験を要する
- 「目的なんか知るか、この技術が使いたい！」っていう手段に対するモチベーションが結果的にその人をその技術のスペシャリストに導く

---
class: middle center

### 「人の役に立つための技術」という考え方ができるかどうかにかかっている
[技術は手段にすぎない。クックパッド勝間氏が語る、いかにして「ユーザーファースト」を実現するか？](http://hrnabi.com/2014/11/14/4882/)

---
class: middle center

## 手段への強いこだわり/情熱がエンジニアをスペシャリストにする

---
class: middle center

- 手段へのこだわりやモチベーションを持たずに、ある文脈での目的に対して最小限の(うわべだけの)技術の使い方で解決するのは嫌だ。
- 自分が置かれている状況を理解していわゆる"大人な選択"をするお行儀の良いエンジニアにはなりたくない。

---
class: middle center

## 手段を知る。手段を知らなきゃ選択できない

???
- 説得できない
- 使うからには普及させる、メンテする覚悟

---
class: middle center

- 最短ルートで効果的に目的を達成するためには良い手段を選べるようになっておくことが大事になる。手段となりうる技術を自分なりに見極めて習得しておいた方が良い
- 有名なサイトが使ってる技術とか、新しいデザインパターンやツール、すぐに使えて今後すぐ有用な技術になりうる新仕様。何をやるべきかなんて答えがないので自分で見極めなきゃいけない

---
class: middle center

## 圧倒的な手段/こだわり持ち、それに固執しない

???
ただ多くの開発現場がチームでプロジェクトを進めていく以上、チームで目的とすることとそれを実現する手段の整合性は重要で、そのためには目的と手段のスコープの切り替えが大事になってくる
- 情熱と俯瞰的な視点のバランス
- 専門性の深さと目的との整合性
- 知っていてこだわらないエンジニアが最終目標

---
class: middle center

## 今は、手段に磨きをかけるフェーズ

???
- 自分はiOSを始め、クライアント開発がとても楽しい
- Rxも使いたい、早くswift3を使いたい

---
class: middle

"技術そのものが好き"という点については有利になることはあれ、不利になることは無いはず  
(!= "技術のことしか考えていない")

???
- 技術そのものが好きでかつ会社のこともちゃんと考えているというエンジニアが求められる

---
class: middle center

ということを踏まえ、改めて。。。

---
class: middle center

# 今後やりたいこと

---
class: middle center

- fastlane
- CIサービス検討
- JSON-RPC
- Realm
- RxSwift/RxAndroid
- AWS Mobile SDK(Cognito/Kinesis/AWS SNS/MobileAnalytice)
- DDDに固執しない
- サーバサイドをちゃんと

???
これらの手段は選択できるように、アンテナを張っています
今回は、軽くfastlaneにのみ話します

---
class: middle center

# [fastlane](https://github.com/fastlane/fastlane)
iOS and Android Automation for Continuous Delivery

???
Continuous Delivery: 継続デリバリー

---
class: middle center

## fastlane is...
- iOS(Android)界隈のトレンドの1つ
- Twitter傘下のFabricに取り込まれており、また幾つかのCIサービスにも標準搭載されるなど今とても勢いのあるツール
- 様々なアクションを組み合わせたレーンを作成し、テストやipaの作成、push通知の証明書、プロビジョニングプロファイルの作成などを簡潔に記述し実行することができる

???
- fastlaneはiOSアプリのビルド、テスト、デプロイを自動化するためのツールチェイン(単体のタスクを実行するプログラムの集合体)
- その他にも、Xcodeのベータテスト配信、Deploygateへの配信、slackへの通知、CIとの連携も簡単に
- こういったフローの自動化はプロジェクト初期にやっておくべき

---
class: middle center

![](http://i1.wp.com/sikmi.com/blog/wp-content/uploads/2016/03/%E6%A7%8B%E6%88%90%E5%9B%B3.png)

---
class: middle center

## ほんの少しだけDemo

1. testを実行 > slackへ
2. screenshot

---
class: middle center

## まとめ
- 高いモチベーションで手段を身につけよう
- それに固執せず、目的との整合性を踏まえた上で選択しよう

---
class: middle center

## See also
- [「技術は手段」について考える](http://blog.h13i32maru.jp/entry/2014/12/27/222939)
- [知っていてこだわらない、それがいいソフトウェアエンジニアの条件なんだと僕は思うんだ](http://a-suenami.hatenablog.com/entry/2016/08/28/130633)
