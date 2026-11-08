# Hi-Fi theme (JamBoard)

**Hi-Fi** is the Home Assistant theme of the Jam look: calm instruments (Jam Design pass 6 + 7). Callsheet paper by day,
navy by night; Jost for words, IBM Plex Mono for small labels and numbers; flat panels with a hairline edge and soft
corners (16px cards, 22px dialogs, 999px pills); no shadows, no glow. Orange is kept for the one thing to do now (at most one
per screen) and red for alerts; state is colour + shape + word. Home Assistant's own switches, sliders and badges take the
house blue, not the orange.

It also defines the `--jam-*` palette that [Jam Cards](https://github.com/Starkkaman/jam-cards) reads. Jam Cards 1.0.0 has
this one look built in: the cards draw Hi-Fi under any theme (without this theme, or under an old Jam theme, they draw the
Night palette from their own values), and with **Hi-Fi** selected they follow its Day and Night palettes.

> Jam Cards 1.0.0 / this release replaced every earlier look. Until then this repo held the Poster theme **JamBoard**
> (`themes/jamboard.yaml`) and the looks Jam Braun, Olympia, Transit, Grid, Pulsar, New Wave, Brutal, Glass, Girard and
> Jam Calm (`themes/jamboard-<look>.yaml`). `themes/jamboard.yaml` keeps its name (HACS keeps installing the same file) and
> now holds **Hi-Fi**; the other files are gone. After the update: run `frontend.reload_themes`, pick **Hi-Fi** in your
> profile, and point the backend default at it (`frontend.set_theme` with `name: Hi-Fi`, once without and once with
> `mode: dark`) if it was JamBoard. A theme name that no longer exists falls back to Home Assistant's default theme. Old
> `jamboard-*.yaml` files that HACS left in `config/themes/` can be deleted; Jam Cards ignores their look either way.

## Palette

| Role | Token | Day | Night |
|---|---|---|---|
| Page ground | `jam-ground` (HA `primary-background-color`) | #efebe2 | #10141d |
| Panel (card face) | `jam-slab`, `jam-paper` | #f9f7f2 | #161c28 |
| Key (control face) | `jam-slab2` | #f1ece2 | #1d2433 |
| Pressed key | `jam-slab3` | #e3dbcb | #0a0e15 |
| Ink (text) | `jam-fg` | #19202e | #ece5d3 |
| Dim text | `jam-dim` | #5b606d | #a29d8f |
| Hairline | `jam-line` | #d6cfbf | #2a3244 |
| The one action | `jam-ochre` | #ec7c22 | #f08a2c |
| Alert fill / text | `jam-red` / `jam-alert-text` | #ff5a48 / #b3261b | #ff5a48 / #ff8a7a |
| Walnut (kiosk rule) | `jam-living` | #6b4428 | #6b4428 |
| ok / warn | `jam-ok` / `jam-warn` | #7bd651 / #f2c14e | #7bd651 / #f2c14e |

Small-switch accents by kind (Jam Design pass 7, option B; a card's `accent` overrides them): plugs / power
`jam-switch-plug` (blue #6780b4 / #5971a4), air / climate `jam-switch-climate` (teal #43899a / #337b8c), automations
`jam-switch-auto` (violet #8f72c0 / #8063b1), settings `jam-switch-set` (steel #71819c / #64738d). Graphs use `jam-s1`..`s5`
(`graph-color-1`..`5`). The calm-instrument parts (fader groove and cap, indicator windows, the purifier's seven-segment
readout and grille dots) have their own `jam-*` tokens; see the comments in `themes/jamboard.yaml`.

Home Assistant's named colours map onto the same hues (`blue`, `teal` / `cyan`, `purple` → violet, `pink`, `green`,
`orange` / `amber` / `yellow` → the orange, `red`).

## Fonts
Home Assistant themes can only set variables; they cannot load web fonts. The theme sets the stacks (`"Jost"` for words,
`"IBM Plex Mono"` for code), and **Jam Cards loads Jost and IBM Plex Mono** when its resource is installed (Jost 400-600
inside the bundle, IBM Plex Mono and a Jost 300 face from its `dist/fonts/`, IBM's files unmodified, SIL OFL 1.1). Without
Jam Cards the stacks fall back to Futura / Century Gothic / the system sans and the system monospace.

## What the theme styles in Home Assistant itself
Soft corners (16px cards and sections, 22px dialogs, 12px controls, 999px badges and pills), a 1px hairline on cards, no
shadows; Jost on cards, headings and card headers; paper / navy surfaces for dialogs, inputs and selects; the house blue for
HA's switches, sliders and primary; named colours, weather icons, graph series, sidebar and app header (#efebe2 / #10141d
with a 1px hairline under the header).

## Dashboard view tabs (needs card-mod)
With [card-mod](https://github.com/thomasloven/lovelace-card-mod) 4.x installed (HACS "lovelace-card-mod", loaded as a
Lovelace resource), the theme restyles Home Assistant's own view tabs in the app header: plain Jost 15px text in the dim
colour, the current tab in ink with a 2px ink underline (the mockup's room tabs). Edit mode keeps Home Assistant's own tab
bar; without card-mod nothing changes. It works through two theme-level keys shared by both modes,
`card-mod-theme: "Hi-Fi"` and `card-mod-root` (CSS that card-mod puts into the dashboard root); to undo it, delete both keys
and run `frontend.reload_themes`. The rules target Home Assistant 2026.10's tab markup (`ha-tab-group` /
`ha-tab-group-tab[data-path]`); a later frontend release that renames those elements makes them stop matching, and the tabs
fall back to Home Assistant's look.

## Generated file
`themes/jamboard.yaml` is generated from the Jam Cards token source (`tokens/` in
[jam-cards](https://github.com/Starkkaman/jam-cards): the token registry, `tokens/looks/hifi.mjs` for this theme and
`tokens/ha.mjs` for the Home Assistant keys derived from the palette) by `node tools/themes.mjs` in jam-cards, with this repo
cloned next to it (`JAM_THEME_DIR=<dir>` writes into another checkout's `themes/`). Do not edit the YAML by hand: change the
token source and regenerate (`node tools/bundle.mjs --check` in jam-cards fails while the YAML is stale).

## Install
HACS → Custom repositories → `Starkkaman/jam-theme`, category **Theme** → Download, then run the `frontend.reload_themes`
action and pick **Hi-Fi** in your profile (or set it as the default theme with `frontend.set_theme`, `name: Hi-Fi`, once
for light and once with `mode: dark`).
