# JamBoard theme

Saul Bass inspired Home Assistant theme: ink and paper with ochre, red and teal; no rounded corners, no shadows;
Jost for text and Londrina Solid for display type.

- Dark mode **ink**: #141210 ground, paper (#ece2c9) text, ochre primary.
- Light mode **paper**: #ece2c9 ground, ink text, red primary (with ink text on it); header and sidebar stay ink.

It also defines the `--jam-*` palette used by [Jam Cards](https://github.com/Starkkaman/jam-cards): ground and slab
colours, the accent hues below, and the series palette `--jam-s1`..`--jam-s5`, which the theme also hands to Home
Assistant's history and statistics graphs (`graph-color-1`..`5`). `--jam-shadow` is still defined for older Jam Cards
versions, but nothing in the theme draws a shadow any more. `--jam-slab3` (#35302a dark, #ddd1b3 light) is the
third surface step: Jam Cards 0.3 use it for inner controls of cards that sit inside a pop-up sheet.
Since the Jam Cards theming work (after 0.7.2) the theme also sets `jam-look: poster` (cards mark themselves with `data-look`) and the fixed ink
colours the cards used to hard-code: `jam-ink-fg` / `jam-ink-dim` / `jam-ink-dim2` (text on ink), `jam-band*` (the ink
bands of the TV / speaker cards, the music dock and the error strip) and `jam-plate` / `jam-plate-fg` (label plates),
the same in both modes. Shape tokens (`jam-shape-*`, `jam-radius-*`) are left to other looks: unset means the JamBoard cuts.
Type tokens (theme top level): `jam-display-weight` (900), `jam-display-case` (uppercase), `jam-display-scale` and
`jam-display-lead` (factors, 1), `jam-label-weight` / `jam-key-weight` (600), `jam-label-case` / `jam-key-case`
(uppercase), `jam-label-track-scale` / `jam-key-track-scale` (factors, 1). The optional `jam-display-track`, `jam-num-font`
and `jam-num-scale` are left to other looks. Lines: `jam-rule-h` (5px accent rule under titles) and `jam-stripe-w` (6px
left tone stripe); `jam-border` (face border) and `jam-art-1`..`8` (idle-art colours) are left to other looks. Motion: `jam-dur` (factor on
every duration, 1), `jam-press-from` / `jam-press` (press transforms); `jam-ease-2/3/4` (timing) and `jam-kf-<name>`
(keyframe names) are left to other looks.

## Accent hues and room colours
Each room has its own hue; red is reserved for alerts. `--jam-on-fg` (#141210 in both modes) is the text colour on
filled accents: every fill hue carries ink text and reaches at least 4.5:1 against it in both modes.

| Token | Dark (ink) | Light (paper) | Used for |
|---|---|---|---|
| `--jam-ochre` | #e5a31b | #d99410 | Living room |
| `--jam-teal` | #22a39a | #22a39a | Kitchen |
| `--jam-blue` | #4a7be0 | #4a7be0 | Master bedroom |
| `--jam-pink` | #e2658f | #d24f7c | Marissa |
| `--jam-violet` | #9b6dd6 | #9b6dd6 | Music |
| `--jam-green` | #86a83a | #6d8f22 | Nerd room |
| `--jam-red` | #e0553b | #e0553b | Alerts only (fills: power keys, alert chips) |
| `--jam-alert-text` | #ff8a6e | #a12a14 | Red text (bad values, "unavailable", "N/A"), >= 4.5:1 on slab/slab2/slab3 |
| `--jam-on-fg` | #141210 | #141210 | Text on filled accents |

Home Assistant's named colours are mapped to the same hues, so tile and button cards that pick a colour by name match
the palette: `blue` → blue, `pink` → pink, `purple` → violet, `green` → green, `teal`/`cyan` → teal,
`amber`/`orange`/`yellow` → ochre, `red` → red.

## Fonts
Home Assistant themes can only set variables; they cannot load web fonts. The theme sets the font stacks
(`"Jost"` for text, `"Londrina Solid"` for display type), and **Jam Cards loads Londrina Solid + Jost** when its
resource is installed. Without Jam Cards the stacks fall back to Helvetica/Arial and Arial Black/Impact.

## What the theme styles in Home Assistant itself
Square corners and no shadows on cards, sections, badges, dialogs (including more-info), tile icons and card
features, pictures and menus; display font on card headers; ink/paper surfaces for dialogs, inputs and selects;
switches, gauge severity (green/yellow/red become teal/ochre/red), named colours (see above), weather icons, graph series,
sidebar and app header.

## Dashboard view tabs (needs card-mod)
With [card-mod](https://github.com/thomasloven/lovelace-card-mod) 4.x installed (HACS "lovelace-card-mod", loaded as a
Lovelace resource), the theme restyles Home Assistant's own view tabs in the app header to match the Jam Tabs card:
Londrina Solid uppercase labels, 48px tall tabs, a 4px bar in the room colour under each tab, the current tab filled
with its room colour and ink text, flat with one 8px cut corner (top right). On the Jam Home dashboard (views
`living`, `kitchen`, `master`, `marissa`, `music`) each tab takes its room hue; tabs on every other dashboard use ochre.
Edit mode keeps Home Assistant's own tab bar. Without card-mod nothing changes.

It works through two theme-level keys, shared by both modes: `card-mod-theme: "JamBoard"` and `card-mod-root` (CSS
that card-mod puts into the dashboard root). To undo it, delete both `card-mod-*` keys and run `frontend.reload_themes`.
The rules target Home Assistant 2026.10's tab markup (`ha-tab-group` / `ha-tab-group-tab[data-path]`); a later
frontend release that renames those elements makes them stop matching, and the tabs fall back to Home Assistant's look.
The Jam Home room hues use CSS `:has()` (Chrome/WebView 105+, Safari 15.4+, Firefox 121+); older browsers show
ochre tabs.

## Jam Olympia (second look)
`themes/jamboard-olympia.yaml` adds the theme **Jam Olympia**, after Otl Aicher's Munich 1972 design: a light ground
(#f4f6f7) with white faces and a 1px hairline (dark mode #10202b / #172b38), square corners, lowercase Albert Sans, and
the Munich spectrum as flat fields and stripes (blue #3a8fd8, light blue #8fc7e8, green #2aa65c, yellow #f6c445, orange
#f08c33, silver). There is no red: alerts are orange. The room hues map onto the spectrum (living orange, kitchen green,
master blue, marissa light blue, music blue, nerd green); text on a filled hue is the deep navy #10202b. Home Assistant
gets a white header and sidebar in light mode, a blue primary and 1px card borders. Jam Cards (with its `dist/fonts/`)
draws the rest: top stripes, square power buttons, spectrum motifs. Pick **Jam Olympia** in your profile, or switch every
browser on "Backend-selected" with `frontend.set_theme` (name `Jam Olympia`, and again with `mode: dark`).

## Jam New Wave (third look)
`themes/jamboard-newwave.yaml` adds the theme **Jam New Wave**, after April Greiman's Design Quarterly #133 (1986) with a
touch of Memphis: a lavender-white page (#fbf8ff; dark #140f2e) with white / indigo planes tinted by their room (pastel
peach, mint, lavender, pink), ink #1b1640 text, a sticker yellow (#fff05a) for alerts, Archivo 700 headings and Silkscreen
pixel numbers and labels, 2px corners. Home Assistant gets a light header with an ink rule, a violet primary and soft card
shadows. Jam Cards (with its `dist/fonts/`) draws the rest: tinted planes, confetti, stickers, pixel bars. The theme sets
`jam-fx: 1`, so the cards also get translucent gradient planes, a slight tilt, blur behind sheets and a drifting light on
the screensaver; on a weak wall tablet set `fx: false` on the jam-kiosk and jam-screensaver cards (flat planes, no tilt).
With card-mod the view tabs become Silkscreen pixel caps with a room-colour underline and an ink block for the current
tab. Pick **Jam New Wave** in your profile, or switch every browser on "Backend-selected" with `frontend.set_theme`.

## Generated file
`themes/jamboard.yaml` is generated from the Jam Cards token source (`tokens/` in
[jam-cards](https://github.com/Starkkaman/jam-cards): the token registry, `tokens/looks/poster.mjs` for this theme and
`tokens/ha.mjs` for the Home Assistant keys derived from the palette) by `node tools/themes.mjs` in jam-cards, with this
repo cloned next to it. Do not edit the YAML by hand: change the token source and regenerate (`node tools/bundle.mjs
--check` in jam-cards fails while the YAML is stale). Further looks are written here as `themes/jamboard-<look>.yaml`:

- `themes/jamboard-braun.yaml` = theme **Jam Braun** (from `tokens/looks/braun.mjs`): after Dieter Rams. Light mode warm
  white (#e7e3da page, #f2efe8 panels, #262626 text), dark mode anthracite (#1c1c1a page, #2a2a27 panels); one orange
  signal (#f07d1e / #f28a2e) as primary and accent of the cards; Archivo, mixed case; 14px radii, a hairline border and a
  soft card shadow (`jam-elev-1`); `jam-look: braun` makes Jam Cards draw toggles, LED dots and the Braun motifs. No
  card-mod view tab styling (HA's own tabs in the theme colours).
- `themes/jamboard-olympia.yaml` = theme **Jam Olympia** (from `tokens/looks/olympia.mjs`); see "Jam Olympia" above.
- `themes/jamboard-newwave.yaml` = theme **Jam New Wave** (from `tokens/looks/newwave.mjs`); see "Jam New Wave" above.

## Install
HACS → Custom repositories → `Starkkaman/jam-theme`, category **Theme** → Download, then run the
`frontend.reload_themes` action and pick **JamBoard** in your profile (or set it as the default theme).
