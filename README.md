# JamBoard theme

Saul Bass inspired Home Assistant theme: ink and paper with ochre, red and teal; no rounded corners, no shadows;
Jost for text and Londrina Solid for display type.

- Dark mode **ink**: #141210 ground, paper (#ece2c9) text, ochre primary.
- Light mode **paper**: #ece2c9 ground, ink text, red primary; header and sidebar stay ink.

It also defines the `--jam-*` palette used by [Jam Cards](https://github.com/Starkkaman/jam-cards), which loads the two
web fonts. Without Jam Cards the fonts fall back to Helvetica/Arial and Impact.

## Install
HACS → Custom repositories → `Starkkaman/jam-theme`, category **Theme** → Download, then run the
`frontend.reload_themes` action and pick **JamBoard** in your profile (or set it as the default theme).
