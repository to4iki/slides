class: center middle
# Naming

2015/10/27

---
class: middle

- Takezawa Toshiki
- twitter: [@to4iki](https://twitter.com/to4iki)
- github: [to4iki](https://github.com/to4iki)
- blog: [to4iki's?.weblog](http://to4iki.hatenablog.jp/)

---
class: middle center

## 戒めを込めて
変数名、Class名に気を使っていますか？  
適当につけてませんか？

---
class: middle center

### この類の話(命名)は今更感があるけど、本当に大事だし、日々考えなければ行けないこと
### 怠惰は許されない

---
class: middle center

そもそも、よい名前とは？

---
class: middle center

よい名前 == よいコード ?

---
## よいコード
- 「他人が読んでわかるコード」が「よいコード」
-  プログラマの仕事は，他のプログラマとの間でコミュニケーションを取ることである。マシンとではない

.right[[Kent Beckの実装パターン](http://to4iki.hatenablog.jp/entry/2015/10/25/231230)]

- コードは他の人が最短で理解できるように書かなければならない

.right[[リーダブルコード](http://to4iki.hatenablog.jp/entry/2015/06/21/124721)]

---
class: middle center
## Example.

---
class: middle center
## get

.right[[単純な話、getであんまり検索したくない](http://d.hatena.ne.jp/jflute/20151020/stopgetselect)]

---
class: middle

- get...は軽いイメージ
    - Javaだと特別なイメージが刷り込まれる
    - \- instance変数を返すだけ
- setも同様

---
class: middle

偏に取得ぽいものといっても色々ある

- `find`
    - 条件に合うものを探し出す
- `fetch`
    - 別の場所から取ってくる - networkごしとか
- `load`
    - 全体を読み込む
- `query`
    - 条件を指定して引き出す
- `extract`
    - 抽出する
- `resolve`
    - 解決する、参照を取得する
- ...

---
class: middle

### よいコードを読み、慣れる事も勿論だが
### 日々、意図が伝わるかを意識する事が大切

---
class: middle

### 気をつけるべきパターンを把握する

---
#### Pattern - 1
- 品詞に気をつける
    - Model(Domein)は名詞にする
        - 二つの単語を繋げてモデルを作る場合は 形容詞 + 名詞 / 名詞 + 名詞にする
    - 処理を実行する関数は動詞のみ / 動詞 + 名詞(目的語)
- データ構造から
    - => 繰り返し: `hasNext / next`
    - => キュー:  `enqueue / dequeue`
- 対称性を意識する
    - => `start / stop`, `head / tail`
- 暗黙的に理解できる所は積極的に省略する
    - `res / tmp`
- 型情報と対応付ける
    - => Boolean: `is~ / has~ / can~`
    - `check~`は広すぎる

---
#### Pattern - 2
- contextを意識する
    - => 非同期: `sync / async`
- scopeの範囲を意識する
    - roopカウンタとかは`i`でも十分伝わる
    - closureでキャプチャリングしている引数も簡略
    ```ruby
    [[1,2], [3,4]].flat_map { |xs| xs << 7 } # [1,2,7,3,4,7]
    (1..5).reduce { |acc, n| acc + n } # 15
    # => (1..5).reduce(:+)
    ```
- DesignPatternなどを参考にする
    - 複雑な生成過程を隠蔽したい `~Factory / ~Generator`
    - 処理を別クラスに委譲させたい `~Delegate`
    - 流れるように(動的に)オブジェクトを生成する `~Builder`

---
#### オマケ(流儀に従う(ex. ボタンハンドラ))
- iOS
    - eventを指定する
    ```java
    button.addTarget(self, action: "onClick", forControlEvents: .TouchUpInside)
    func onClick() {}
    ```

- Android
    - Click用のListnerが用意されている
    ```java
    button.setOnClickListener(new View.OnClickListener() {
      public void onClick(View v) {}
    });
    ```

---
class: middle center

### 最初から抽象的な命名をする事は難しい
### 抽象と具象のバランス感覚

---
class: middle

### アンチパターンを知る事がよい命名付けのヒントになる
- 不吉なにおいを嗅ぎ取れるようなる
- よい設計のヒントになる

---
#### アンチパターンを意識する - 1
- `UserData / UserInfo`
    - 広すぎる
    - => `UserAttributes / UserProperties`

- `ProductListItem`
    - 冗長
    - => `Products`

---
#### アンチパターンを意識する - 2
- `TimeUtil / StringHelper`
    - 単一責任の原則から外れがち、Godクラスに昇格してしまう恐れ
    - 本来instance化すべきクラスの寄せ集めになってしまう
    - instance化することに意味があるなら具体的モノの名前を付ける
    - `~Manager`とかも同じ、適切な役割に基づいた名前を再考する

- `applicationShouldTerminateAfterLastWindowClosed`
    - 長すぎると本質が失われるのでは / 無理にまとめない
    - 余計なprefixはいらない(＊namespaceが無い環境はしようが無い)

---
class: middle center

### まとめ

---
class: middle center

### 名前がよい => 意図が伝わる => よいコード

---
### 身につけるため
- Code Reviewしてもらう
    - メソッド名で意図を表現すれば、Reviewで間違いを見つけてもらいやすくなる
- BuiltInクラス、OSSのCodeを参考にする
- DesignPatternなどから引用する
- こまめに辞書を引く

---
### see also
- [naming - ネーミングのルール - Qiita](http://qiita.com/goforbroke/items/48d8de96859aed087e88)
- [設計 - クラスの命名のアンチパターン - Qiita](http://qiita.com/magicant/items/8134edf969f9629fa66e)
- [プログラミング - うまくメソッド名を付けるための参考情報 - Qiita](http://qiita.com/KeithYokoma/items/2193cf79ba76563e3db6)
- [読み物 - コードを書く際の指針として見返すサイトまとめ - Qiita](http://qiita.com/kenichi_cc/items/c3ecca7b7d5fc5c6bf2e)
- [プログラミングで変数名や関数名のネーミングに迷ったときに便利なカンニングペーパーまとめ](http://nelog.jp/programming-words)

---
class: center, middle

オマケ

<blockquote class="twitter-tweet" lang="ja"><p lang="ja" dir="ltr">基本的に同意なんだけども、DB検索をモナドにすれば名前なんて何でもよｋ（ここで文章は途切れている <a href="https://t.co/G8VhHFxNCK">https://t.co/G8VhHFxNCK</a></p>&mdash; がくぞ (@gakuzzzz) <a href="https://twitter.com/gakuzzzz/status/656821958395367424">2015, 10月 21</a></blockquote>
