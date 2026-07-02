# capsule-native.github.io

GitHub Pages site for **Capsule** — a native macOS app for Apple's `container` CLI. This repo
hosts the landing page and the **Sparkle appcast** the app polls for auto-updates.

- **Appcast feed:** <https://capsule-native.github.io/appcast.xml> — this is the app's `SUFeedURL`.
- `appcast.xml` is generated and **EdDSA-signed** by the release pipeline in
  [`capsule-native/capsule`](https://github.com/capsule-native/capsule) and attached to each
  GitHub Release. The [**Deploy Pages**](.github/workflows/deploy.yml) workflow here fetches that
  signed `appcast.xml` from the latest release **at deploy time** and ships it with the site — no
  commit — then publishes via GitHub Pages.

The site is deployed by our own GitHub Actions workflow (Pages source = **GitHub Actions**), not
the built-in Jekyll builder, so we control the action versions and the deploy step. It runs on
every push to `main`, on a ~15-minute schedule (to pick up new releases), and on demand.

> The committed `appcast.xml` is only a placeholder — the deploy overwrites it with the latest
> release's signed feed. To publish immediately after cutting a release, run **Deploy Pages**
> (Actions ▸ Deploy Pages ▸ Run workflow); otherwise the schedule refreshes it within ~15 minutes.
