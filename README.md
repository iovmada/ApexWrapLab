# Symbiot — static preview

Single self-contained `index.html` (CSS inlined, images as data URIs, no external
scripts). Snapshot of the WooCommerce theme running locally on :8790, with a tab
bar for: home · shop · filtered shop · product · accessory.

Deployed as a **DigitalOcean App Platform static site** (free Starter tier).

## Refresh the snapshot

Re-generate `docs/preview.html` from the local WP install, then:

    cp ../docs/preview.html index.html && git commit -am "refresh preview" && git push

App Platform redeploys on push to `main`.
