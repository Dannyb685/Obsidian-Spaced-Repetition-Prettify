# Prettify Nord for Obsidian Spaced Repetition

A CSS snippet that restyles the [Obsidian Spaced Repetition](https://github.com/st3v3nmw/obsidian-spaced-repetition) review view to look like Anki's Prettify theme in Nord colors.

This is a port. The design is [Prettify by Deshai Pranav](https://github.com/pranavdeshai/anki-prettify), written for Anki. Anki and Obsidian share no class names, so none of the original CSS applies to Obsidian as-is. This repo rewrites it against the classes the Obsidian plugin actually uses, keeping the same look.

## What it changes

- The review card becomes a white (or `#2e3440`) rounded card on a Nord background, centered at 40em with a soft shadow
- Rubik at 26px, falling back to the system font stack
- Cloze deletions get the Prettify highlight: red on pale yellow in light mode, Nord blue in dark
- The front/back divider, image hover-to-zoom, tables, and links all follow the Nord palette
- Answer buttons take the Nord grades: Again `#bf616a`, Hard `#d08770`, Good `#a3be8c`, Easy `#88c0d0`

Light and dark are both handled. Everything is scoped to `.sr-view` and `#sr-modal-view`, so the rest of your vault is untouched.

## Install

1. Download `prettify-nord-spaced-repetition.css`
2. Drop it in `YourVault/.obsidian/snippets/`
3. Settings → Appearance → CSS snippets → reload, then toggle it on

## Tweaking it

The variables at the top of the file are the ones worth touching:

| Variable | Default | Notes |
| --- | --- | --- |
| `--font-size-regular` | `26px` | Anki-sized. Drop to ~18px if it feels large in a tab. |
| `--card-max-width` | `40em` | Card width. |
| `--card-text-align` | `left` | `center` matches stock Anki. |
| `--img-width` | `90%` | Images expand to full width on hover. |

The Nord button colors sit in their own labeled block. Delete it to get the plugin's default red/orange/blue/green back.

## Two optional blocks near the end

Both assume you have remapped the plugin's review keys to Anki's order (Again=1, Hard=2, Good=3, Easy=4). On a stock install, delete them.

**Key badges.** Relabels the small key hints on the answer buttons to `1 2 3 4`. On a stock install the real keys are Hard=1, Good=2, Easy=3, so these labels would lie to you.

**Grade flash.** A colored tick appears in the bottom-left of the card for 0.2s when you grade with a key, matching that button's color. This one also needs a small patch to the plugin's `main.js` to create the element. Without it the CSS is inert and harmless. Tune the timing with `--tick-duration`.

One thing worth knowing regardless of whether you use this theme: the plugin ships a `0` badge on the Again button, but pressing `0` fires **Reset**, which wipes that card's scheduling history with no confirmation. Again has no key at all. That badge is wrong as shipped.

## Notes

- Literal `<b>` tags are left alone on purpose, so click-to-reveal cloze snippets keep working. Only markdown `**bold**` is recolored.
- Anki's deck breadcrumb and tag pills have no direct equivalent in the Obsidian plugin. Those styles map onto the plugin's context line instead.
- Rubik is referenced but not bundled. Without it installed, the snippet falls back to the system font.

## Credit

The visual design is entirely [Deshai Pranav's](https://github.com/pranavdeshai). If you use this, go star [anki-prettify](https://github.com/pranavdeshai/anki-prettify) — and if you use Anki, use the original.

- Original: [pranavdeshai/anki-prettify](https://github.com/pranavdeshai/anki-prettify) (MIT)
- [Buy them a coffee](https://www.buymeacoffee.com/pranavdeshai) · [Ko-fi](https://ko-fi.com/pranavdeshai)

Nord palette by [Arctic Ice Studio](https://www.nordtheme.com/).

## License

MIT. See [LICENSE](LICENSE) — the original copyright notice is retained.
