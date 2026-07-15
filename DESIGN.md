# Design

## Visual Theme

Dark instrument panel. The live camera frame dominates; all chrome sits on near-black surfaces that read as hardware bezel, not app UI. Blackmagic-style technical density: small caps labels, tabular numerals, hairline separators. No cards, no shadows, no glass. Color appears only as measurement-channel coding.

## Color Palette

Neutrals (OKLCH, hue-tinted toward warm yellow to match the brand accent):

- `--bg`: oklch(0.13 0.006 95) — app background / bezel
- `--surface`: oklch(0.16 0.006 95) — bars and panels
- `--line`: oklch(0.24 0.006 95) — hairline separators
- `--text`: oklch(0.92 0.008 95) — primary values
- `--text-dim`: oklch(0.62 0.008 95) — labels, sublines
- `--text-faint`: oklch(0.45 0.006 95) — footnote/meta

Channel colors (each bound to exactly one measurement, used for its button state, overlay marks, and readout value):

- Key / ratio: `#f5c518` (yellow)
- Fill: `#4aa3ff` (blue)
- Background sep: `#c78bff` (purple)
- Spot: `#ff6ea9` (pink)
- CCT: `#ff9a6a` (orange)
- Face auto: `#7ee87e` (green)
- EV: `#8fd0ff` (ice)
- Alert/clip: `#e0403c` (red, false-color toggle + errors only)

## Typography

System stack: -apple-system, 'SF Pro', Roboto, sans-serif.

- Measurement values: 26px, weight 700, `font-variant-numeric: tabular-nums`, tight letter-spacing
- Value units/suffix: same line, 60% size, text-dim
- Channel labels: 10px, uppercase, letter-spacing 1.2px, text-dim
- Sublines (stops, labels): 11px, text-dim
- Buttons: 12-13px, weight 600
- Hierarchy contrast ratio between value and label ≥ 2.4x

## Components

- Mode bar: single row of flat segmented buttons, 44px tall, active state = channel color fill with dark text, inactive = surface with dim text, 1px hairline between segments, no gaps.
- Readout strip: one horizontal instrument row (not a card grid): each channel is a column of label-over-value separated by hairlines. Wraps to 2 rows only under 360px.
- Header: app mark left, utility toggles right (FC / Flip / AE / Reset) as compact 44px flat buttons.
- Overlay marks: 2px strokes in channel color, 12px bold canvas labels with 1px dark offset for legibility.
- Hint line: single 12px line over the viewfinder bottom, text-shadowed, never wraps to more than one line.
- Gel panel: inline drawer under the mode bar, same surface, hairline top border. Chips are flat 44px-tall toggles.

## Layout

- Full-bleed viewfinder between header and bottom control stack; controls live in the bottom third (thumb zone).
- Spacing scale: 4 / 8 / 12 / 16. Bars use 12px vertical padding; readout columns 10px.
- Safe-area insets respected top and bottom.
- No rounded-corner inflation: radius 6px max on interactive elements, 0 on bars.

## Motion

- Value changes: none (numbers update in place; motion would read as instability).
- Panel open/close (gel drawer): 180ms ease-out-quart height/opacity, disabled under prefers-reduced-motion.
- Button state: 120ms background ease-out. No transforms, no bounce.
