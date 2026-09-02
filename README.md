# ApexWrapLab — static site

`index.html` — the home page, implemented from the Claude Design canvas
**"Apex Racing Livery Redesign"** (`Apex Home.dc.html`), project
`a1bd101a-780f-434d-8a49-5267a8055727`.

Deployed as a **DigitalOcean App Platform static site** (free Starter tier) at
apexwraplab.com. Every push to `main` redeploys.

## What was translated

The canvas is not a runnable page — it targets a React runtime (`support.js`)
with `{{ }}` bindings, `sc-for` / `sc-if` control flow, `style-hover`
attributes and an `<image-slot>` custom element. None of that ships. Instead:

- `sc-for` / `sc-if` expanded against the data in the canvas `DCLogic` class
- `{{ }}` bindings resolved; `style-hover` rewritten as real CSS `:hover`
- `<image-slot>` replaced by `<img>` inside a `.slot` wrapper
- behaviour reimplemented in vanilla JS: EN/RO toggle (`data-ro`), dark/light
  theme, fitment selects, configurator (colour × pattern × finish → preview +
  price), IntersectionObserver scroll reveal

Design tokens, type scale and copy are carried over verbatim.

## Images — currently missing

The 12 images the page references are **not in this repo**. `DesignSync`'s
`get_file` caps at 256 KiB and every PNG came back `truncated=true` with no
`IEND` chunk, so shipping them would have meant shipping corrupt files.

Each `.slot` falls back to a designed gradient, so the layout is complete
without them. To add the real ones, drop these into `images/` — the filenames
are already wired up, no code change needed:

    hero-livery.png   config-base.png
    kit-apex-predator.png   kit-factory-replica.png
    kit-crimson-stealth.png kit-volt-surge.png
    ig-1.png … ig-6.png

## Not built yet

`Apex Shop.dc.html` is a second artboard in the same canvas. It is not
implemented — nav/footer links that pointed at it now go to `#kits`.

## Also here

`wp-preview.html` — the earlier WooCommerce theme snapshot, kept for reference.
