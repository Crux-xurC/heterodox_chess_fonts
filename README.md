# heterodox_chess_fonts

A chess-piece font for fairy-chess variants. It contains 52 glyphs: 13 piece types, each in four variants, assigned to the Private Use Area range U+E900–U+E933.

![Specimen showing all glyphs](specimen.png)

Rows are, from top to bottom: white outline upright, black filled upright, white outline rotated 180°, and black filled rotated 180°.

## Files

| File | Contents |
|---|---|
| `heterodox_chess.ttf` | The font to use in applications |
| `heterodox_chess.sfd` | FontForge source. Edit this file and export a new TTF when changing the font |
| `names.json` | Canonical glyph name to code point mapping, such as `"king_w": "U+E900"` |
| `mozc_dictionary.txt` | User dictionary for Mozc. Readings are Japanese kana piece names; comments are the canonical names |
| `specimen.png` | Glyph specimen |
| `OFL.txt` | Full text of the SIL Open Font License 1.1 |

## Code point and glyph names

```
code point = 0xE900 + 4 × (piece number − 1) + (variant number − 1)
```

Each glyph has the canonical name `<piece>_<variant>`. The font uses the same glyph names, and `names.json` maps each name to a code point.

| Variant | Suffix | Description |
|---|---|---|
| 1 | `w` | White outline, upright |
| 2 | `b` | Black filled, upright |
| 3 | `rw` | White outline, rotated 180° |
| 4 | `rb` | Black filled, rotated 180° |

| Piece # | Piece | w | b | rw | rb |
|---:|---|---|---|---|---|
| 1 | king | `king_w` U+E900 | `king_b` U+E901 | `king_rw` U+E902 | `king_rb` U+E903 |
| 2 | queen | `queen_w` U+E904 | `queen_b` U+E905 | `queen_rw` U+E906 | `queen_rb` U+E907 |
| 3 | rook | `rook_w` U+E908 | `rook_b` U+E909 | `rook_rw` U+E90A | `rook_rb` U+E90B |
| 4 | bishop | `bishop_w` U+E90C | `bishop_b` U+E90D | `bishop_rw` U+E90E | `bishop_rb` U+E90F |
| 5 | knight | `knight_w` U+E910 | `knight_b` U+E911 | `knight_rw` U+E912 | `knight_rb` U+E913 |
| 6 | pawn | `pawn_w` U+E914 | `pawn_b` U+E915 | `pawn_rw` U+E916 | `pawn_rb` U+E917 |
| 7 | nightrider | `nightrider_w` U+E918 | `nightrider_b` U+E919 | `nightrider_rw` U+E91A | `nightrider_rb` U+E91B |
| 8 | madman | `madman_w` U+E91C | `madman_b` U+E91D | `madman_rw` U+E91E | `madman_rb` U+E91F |
| 9 | peasant | `peasant_w` U+E920 | `peasant_b` U+E921 | `peasant_rw` U+E922 | `peasant_rb` U+E923 |
| 10 | guard | `guard_w` U+E924 | `guard_b` U+E925 | `guard_rw` U+E926 | `guard_rb` U+E927 |
| 11 | researcher | `researcher_w` U+E928 | `researcher_b` U+E929 | `researcher_rw` U+E92A | `researcher_rb` U+E92B |
| 12 | standard | `standard_w` U+E92C | `standard_b` U+E92D | `standard_rw` U+E92E | `standard_rb` U+E92F |
| 13 | scout | `scout_w` U+E930 | `scout_b` U+E931 | `scout_rw` U+E932 | `scout_rb` U+E933 |

The allocation starts at U+E900 to avoid collisions with other fonts using the U+E000 range, including Adwaita Sans, MathJax, and Nerd Fonts. Browsers based on Chromium do not search fallback fonts for Private Use Area characters, so specify this font with `font-family`.

## Dimensions

- The em square is 1024 units; every glyph has an advance width of 1024, and the cell is square.
- Rotated variants are rotated 180° around the center of the em square, so they occupy the same cell as their upright variants.

## CSS example

```css
@font-face {
  font-family: "HeterodoxChess";
  src: url("fonts/heterodox_chess.ttf") format("truetype");
  font-display: swap;
}
.square { font-family: "HeterodoxChess", serif; }
```

```js
// piece number: 1–13; variant number: 1–4
const glyph = String.fromCharCode(0xE900 + 4 * (piece - 1) + (variant - 1));

// Look up a glyph by name after loading names.json.
const ch = (name) => String.fromCodePoint(parseInt(names[name].slice(2), 16));
ch("king_w");
```

## License

Copyright (c) 2026, Crux-xurC

Licensed under the [SIL Open Font License 1.1](OFL.txt). You may use, modify, redistribute, and bundle the font with software, including commercial software. Do not sell the font by itself. Include the copyright notice and license when redistributing it; modified versions must remain under the OFL.
