# heterodox_chess_fonts

フェアリーチェス（変則チェス）の駒のフォント。13駒 × 4種の52グリフを、私用領域 U+E000〜U+E033 に置いている。

![駒の一覧](specimen.png)

上の行から 白抜き正立・黒塗り正立・白抜き 180° 回転・黒塗り 180° 回転。

## ファイル

| ファイル | 中身 |
|---|---|
| `heterodox_chess.ttf` | 使う側が読むフォント |
| `heterodox_chess.sfd` | FontForge の元データ。直すときはこちらを直して ttf を書き出す |
| `names.json` | 正式名称 → コードポイント（`"king_w": "U+E000"` の形） |
| `specimen.png` | 上の一覧 |
| `OFL.txt` | ライセンスの全文（SIL Open Font License 1.1） |

## 文字の割り当てと名前

```
コードポイント = 0xE000 + 4 × (駒番号 − 1) + (種類 − 1)
```

それぞれの字には `<駒の名前>_<種類>` の正式名称がある。フォントの中のグリフ名もこの名前で、
名前からコードポイントへの対応は `names.json` にある。

| 種類 | 接尾辞 | 意味 |
|---|---|---|
| 1 | `w` | 白抜き正立 |
| 2 | `b` | 黒塗り正立 |
| 3 | `rw` | 白抜き 180° 回転（rotated white） |
| 4 | `rb` | 黒塗り 180° 回転（rotated black） |

| 駒番号 | 駒 | w | b | rw | rb |
|---|---|---|---|---|---|
| 1 | king | `king_w` U+E000 | `king_b` U+E001 | `king_rw` U+E002 | `king_rb` U+E003 |
| 2 | queen | `queen_w` U+E004 | `queen_b` U+E005 | `queen_rw` U+E006 | `queen_rb` U+E007 |
| 3 | rook | `rook_w` U+E008 | `rook_b` U+E009 | `rook_rw` U+E00A | `rook_rb` U+E00B |
| 4 | bishop | `bishop_w` U+E00C | `bishop_b` U+E00D | `bishop_rw` U+E00E | `bishop_rb` U+E00F |
| 5 | knight | `knight_w` U+E010 | `knight_b` U+E011 | `knight_rw` U+E012 | `knight_rb` U+E013 |
| 6 | pawn | `pawn_w` U+E014 | `pawn_b` U+E015 | `pawn_rw` U+E016 | `pawn_rb` U+E017 |
| 7 | nightrider | `nightrider_w` U+E018 | `nightrider_b` U+E019 | `nightrider_rw` U+E01A | `nightrider_rb` U+E01B |
| 8 | madman | `madman_w` U+E01C | `madman_b` U+E01D | `madman_rw` U+E01E | `madman_rb` U+E01F |
| 9 | peasant | `peasant_w` U+E020 | `peasant_b` U+E021 | `peasant_rw` U+E022 | `peasant_rb` U+E023 |
| 10 | guard | `guard_w` U+E024 | `guard_b` U+E025 | `guard_rw` U+E026 | `guard_rb` U+E027 |
| 11 | researcher | `researcher_w` U+E028 | `researcher_b` U+E029 | `researcher_rw` U+E02A | `researcher_rb` U+E02B |
| 12 | standard | `standard_w` U+E02C | `standard_b` U+E02D | `standard_rw` U+E02E | `standard_rb` U+E02F |
| 13 | scout | `scout_w` U+E030 | `scout_b` U+E031 | `scout_rw` U+E032 | `scout_rb` U+E033 |

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

// 名前から（names.json を読んで）
const ch = (name) => String.fromCodePoint(parseInt(names[name].slice(2), 16));
ch("king_w");
```

## ライセンス

Copyright (c) 2026, Crux-xurC

[SIL Open Font License 1.1](OFL.txt)。誰でも、商用も含めて、使用・改変・再配布・ソフトウェアへの同梱ができる。
条件は、フォント単体で売らないこと、再配布するときに著作権表示とこのライセンスを付けること、改変版も同じライセンスにすること。
