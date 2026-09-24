# w3f-media

The files offered for download on [w3ltfrieden.org/materials](https://w3ltfrieden.org/de/materials).

**Everything in this repository is public**, including every release asset, whether or not the
manifest lists it.

## How the site reads it

- `manifest.json` decides what the page shows: the cards in each section (`documents`, `press`),
  their title and description in German and English, and the files on each card with their link
  labels.
- The files themselves are assets on the releases of this repository. The site links each file
  name to the newest published release that carries an asset with that name.
- The site picks up a change within five minutes. Nothing needs deploying.
- A file the manifest names but no published release carries is left off the page. A card with no
  file left is left off too. The `Check manifest` workflow fails in both cases, so look there after a
  change.
- Format and size on the page come from the release asset, so the manifest never states them.

## Add a file

1. Name it in lowercase letters, digits and hyphens, ending in `.pdf`, `.zip`, `.png` or `.jpg`,
   for example `w3ltfrieden-expose-de.pdf`. The name is the link: `w3ltfrieden.org/downloads/<name>`.
2. Publish a release with the file as an asset. Tag it with the date, `2026-09-24`, and add `-2`
   for a second release on the same day.

   ```bash
   gh release create 2026-09-24 w3ltfrieden-expose-de.pdf --title "Exposé" --notes "Exposé, German"
   ```

3. Add the file to a card in `manifest.json`, or add a new card, and push to `main`.

Publish the release before you push the manifest, or the check fails until the release exists.

## Replace a file

Publish a new release carrying a file with the same name. The site links the newest one. The older
release stays reachable at its own GitHub URL until you delete that asset.

## Remove a file

Delete its entry from `manifest.json`. To take the file offline as well, delete the asset from
every release that carries it.

## Limits

GitHub accepts files up to 2 GiB. A draft release is ignored by the site.
