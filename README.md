# JamBoard theme

Saul Bass inspired Home Assistant theme: ink and paper with ochre, red and teal; no rounded corners, no shadows;
Jost for text and Londrina Solid for display type.

- Dark mode **ink**: #141210 ground, paper (#ece2c9) text, ochre primary.
- Light mode **paper**: #ece2c9 ground, ink text, red primary; header and sidebar stay ink.

It also defines the `--jam-*` palette used by [Jam Cards](https://github.com/Starkkaman/jam-cards): ground and slab
colours, the accent hues below, and the series palette `--jam-s1`..`--jam-s5`, which the theme also hands to Home
Assistant's history and statistics graphs (`graph-color-1`..`5`). `--jam-shadow` is still defined for older Jam Cards
versions, but nothing in the theme draws a shadow any more.

## Accent hues and room colours
Each room has its own hue; red is reserved for alerts. `--jam-on-fg` (#141210 in both modes) is the text colour on
filled accents.

| Token | Dark (ink) | Light (paper) | Used for |
|---|---|---|---|
| `--jam-ochre` | #e5a31b | #d99410 | Living room |
| `--jam-teal` | #22a39a | #14897f | Kitchen |
| `--jam-blue` | #4a7be0 | #3563c9 | Master bedroom |
| `--jam-pink` | #e2658f | #d24f7c | Marissa |
| `--jam-violet` | #9b6dd6 | #8657c4 | Music |
| `--jam-green` | #86a83a | #6d8f22 | Nerd room |
| `--jam-red` | #d8432a | #c2361a | Alerts only |
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

## Install
HACS → Custom repositories → `Starkkaman/jam-theme`, category **Theme** → Download, then run the
`frontend.reload_themes` action and pick **JamBoard** in your profile (or set it as the default theme).
