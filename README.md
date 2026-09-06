# notification-banner-re-reloaded
Fork of the original Gnome Shell extension allowing customization of notification banner position and animation properties

## Installation

### Install from GNOME Extensions

<a href="https://extensions.gnome.org/extension/10222/notification-banner-re-reloaded/">
  <img src="https://github.com/user-attachments/assets/d15de748-11b8-4a85-ad34-ec7786547b3c" width="250" alt="Install from GNOME Extensions">
</a>

> ⚠️ Due to the review process, the version on GNOME Extensions may lag behind the latest code in this repository.  
> For the newest features, it is recommended to install manually from this branch.  
> If you’d like to try the latest (possibly unstable) features, you can switch to the `experimental` branch.
  
### Manual

1. Clone the repository:

   ```bash
   git clone https://github.com/chrishuan9/notification-banner-re-reloaded.git
   ```
2. Copy to your extensions folder:

   ```bash
   cp -r notification-banner-re-reloaded ~/.local/share/gnome-shell/extensions/notification-banner-re-reloaded@chrhuang
   ```
3. Log out and back in, then enable the extension:

   ```bash
   gnome-extensions enable notification-banner-re-reloaded@chrhuang
   ```
4. Open the extension preferences and setup the position of the notification banner

## Requirements
* recompile schema if adding additional options: <br>
  ```glib-compile-schemas schemas```

## Releasing

Releases are automated via [GitHub Actions](.github/workflows/release.yml). To cut a new release:

```bash
git tag vX.Y.Z
git push origin vX.Y.Z
```

Pushing a `v*.*.*` tag will:
1. Recompile `schemas/gschemas.compiled` from the `.gschema.xml` (so a forgotten local recompile never ships a stale schema).
2. Set `metadata.json`'s integer `version` field to the tag's major number (e.g. `v12.0.0` → `12`).
3. Package `extension.js`, `prefs.js`, `utils.js`, `metadata.json` and `schemas/` into a zip — deliberately excluding `icon.png`, `README.md`, `LICENSE`, and `.github/`, since GNOME Extensions rejects/doesn't want those in the uploaded zip.
4. Create a GitHub Release with that zip attached and auto-generated release notes (the changelog) from the commits/PRs since the last tag.

The resulting zip is what you upload to [extensions.gnome.org](https://extensions.gnome.org/upload/) — note that e.g.o assigns and displays its own review-queue version number independent of the `version` in the zip's `metadata.json`.

## Acknowledgments
* Original Author of [notification-position-reloaded](https://github.com/marcinjakubowski/notification-position-reloaded)
* Icon kindly provided by Flaticon: <a href="https://www.flaticon.com/free-icons/subscribe" title="subscribe icons">Subscribe icons created by Freepik - Flaticon</a>
