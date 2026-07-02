# capsule-native.github.io

GitHub Pages site for **Capsule** — a native macOS app for Apple's `container` CLI. This repo
hosts the landing page and the **Sparkle appcast** the app polls for auto-updates.

- **Appcast feed:** <https://capsule-native.github.io/appcast.xml> — this is the app's `SUFeedURL`.
- `appcast.xml` is generated and **EdDSA-signed** by the release pipeline in
  [`capsule-native/capsule`](https://github.com/capsule-native/capsule) and attached to each
  GitHub Release. The [**Sync appcast**](.github/workflows/sync-appcast.yml) workflow here pulls
  the latest release's `appcast.xml` and commits it, which republishes the feed via Pages.

> Do not edit `appcast.xml` by hand — the sync workflow overwrites it. To publish immediately
> after cutting a release, run the **Sync appcast** workflow (Actions ▸ Sync appcast ▸ Run
> workflow); otherwise it syncs automatically within ~15 minutes.
