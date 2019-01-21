# vertical-wriiting-for-iOS
縦書きの闇をあるていど回避する

## 結論
全角変換してフォントを Hiragino に指定する。
line height を設定する。 (font.height あたり)

ただし、「ｲﾞ」などの濁音の半角カタカナの一部は「"」部分が下に描画されてしまう問題がある。
(もしかしたら、全角に変換したときにそのまま全角にできずに「イ」と「”」に分割されているのでは。)

## 何があったか

### TTTAttributedLabel
単に縦書きしたいだけなら使わなくて良い気がする。
そんなに大変さは変わらないことや、縦書きのような闇の多い実装には変な挙動はつきものなので、なるべく自分で把握できる方法をとりたい。(実際に空白かサイズか何かで問題が起きてライブラリの中を探って消耗してやめた)

### フォントについて
#### System font に設定した場合
記号が縦にならない。縦書きのグリフが入っていないのでは疑惑。

#### Hiragino に設定した場合
記号の縦書きに対応できたが欧文が縦にならない。

#### 欧文を System font、それ以外を Hiragino にする
半角カタカナに対応できない。

### 行間が一行分くらい開く
lineHeight を明示的に設定する
