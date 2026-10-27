# JamBoard theme

Saul Bass inspired Home Assistant theme: ink and paper with ochre, red and teal; no rounded corners, no shadows;
Jost for text and Londrina Solid for display type.

- Dark mode **ink**: #141210 ground, paper (#ece2c9) text, ochre primary.
- Light mode **paper**: #ece2c9 ground, ink text, red primary; header and sidebar stay ink.

It also defines the `--jam-*` palette used by [Jam Cards](https://github.com/Starkkaman/jam-cards): ground and slab
colours, ochre/red/teal state tones, `--jam-shadow` (the flat paper shadow slab) and the series palette
`--jam-s1`..`--jam-s5`, which the theme also hands to Home Assistant's history and statistics graphs
(`graph-color-1`..`5`).

## Fonts
Home Assistant themes can only set variables; they cannot load web fonts. The theme sets the font stacks
(`"Jost"` for text, `"Londrina Solid"` for display type), and **Jam Cards loads Londrina Solid + Jost** when its
resource is installed. Without Jam Cards the stacks fall back to Helvetica/Arial and Arial Black/Impact.

## What the theme styles in Home Assistant itself
Square corners and no shadows on cards, sections, badges, dialogs (including more-info), tile icons and card
features, pictures and menus; display font on card headers; ink/paper surfaces for dialogs, inputs and selects;
switches, gauge severity (green/yellow/red become teal/ochre/red), weather icons, graph series, sidebar and app header.

## Install
HACS → Custom repositories → `Starkkaman/jam-theme`, category **Theme** → Download, then run the
`frontend.reload_themes` action and pick **JamBoard** in your profile (or set it as the default theme).
