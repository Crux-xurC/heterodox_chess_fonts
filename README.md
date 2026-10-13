# heterodox_chess_fonts

フェアリーチェス（変則チェス）の駒のフォント。13駒 × 4種の52グリフを、私用領域 U+E000〜U+E033 に置いている。

![駒の一覧](specimen.png)

上の行から 白抜き正立・黒塗り正立・白抜き 180° 回転・黒塗り 180° 回転。

## ファイル

| ファイル | 中身 |
|---|---|
| `heterodox_chess.ttf` | 使う側が読むフォント |
| `heterodox_chess.sfd` | FontForge の元データ。直すときはこちらを直して ttf を書き出す |
| `specimen.png` | 上の一覧 |
| `LICENSE` | ライセンスの全文（The Unlicense） |

## 文字の割り当て

```
コードポイント = 0xE000 + 4 × (駒番号 − 1) + (種類 − 1)
```

種類は 1 = 白抜き正立、2 = 黒塗り正立、3 = 白抜き 180° 回転、4 = 黒塗り 180° 回転。

| 駒番号 | 駒 | 白抜き正立 | 黒塗り正立 | 白抜き回転 | 黒塗り回転 |
|---|---|---|---|---|---|
| 1 | king | U+E000 | U+E001 | U+E002 | U+E003 |
| 2 | queen | U+E004 | U+E005 | U+E006 | U+E007 |
| 3 | rook | U+E008 | U+E009 | U+E00A | U+E00B |
| 4 | bishop | U+E00C | U+E00D | U+E00E | U+E00F |
| 5 | knight | U+E010 | U+E011 | U+E012 | U+E013 |
| 6 | pawn | U+E014 | U+E015 | U+E016 | U+E017 |
| 7 | nightrider | U+E018 | U+E019 | U+E01A | U+E01B |
| 8 | madman | U+E01C | U+E01D | U+E01E | U+E01F |
| 9 | peasant | U+E020 | U+E021 | U+E022 | U+E023 |
| 10 | guard | U+E024 | U+E025 | U+E026 | U+E027 |
| 11 | researcher | U+E028 | U+E029 | U+E02A | U+E02B |
| 12 | standard | U+E02C | U+E02D | U+E02E | U+E02F |
| 13 | scout | U+E030 | U+E031 | U+E032 | U+E033 |

## 寸法

- em は 1024。全グリフの送り幅が 1024 で、升目は正方形
- 回転版は em の中心で 180° 回してあるので、正立と同じ升目に収まる

## 使い方（CSS）

```css
@font-face {
  font-family: "HeterodoxChess";
  src: url("fonts/heterodox_chess.ttf") format("truetype");
  font-display: swap;
}
.square { font-family: "HeterodoxChess", serif; }
```

```js
// 駒番号 piece（1〜13）、種類 variant（1〜4）
const glyph = String.fromCharCode(0xE000 + 4 * (piece - 1) + (variant - 1));
```

## ライセンス

[The Unlicense](LICENSE)。パブリックドメインに置いている。誰でも、商用も含めて、条件なしで使用・改変・再配布・販売ができる。
