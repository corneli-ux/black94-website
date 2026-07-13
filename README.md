# Black94 Website

Marketing site for [black94.com](https://black94.com) — the companion Flutter app lives in [black94-app](https://github.com/corneli-ux/black94-app).

## Structure

Plain static HTML/CSS/JS, no build step:

```
public/
  index.html       - main marketing page
  privacy.html     - Privacy Policy (already submitted to Indus App Store - keep this URL working)
  terms.html       - Terms of Service
  style.css        - shared stylesheet, matches the app's exact brand (black background, purple/cyan gradient, Inter)
  assets/          - logo/icon assets, copied directly from the app's own brand assets
```

## Deployment

Deploys to Firebase Hosting, project `memora-bond` (same project the app repo's Firestore/Functions/Storage already use, and the same one `black94.com`'s DNS is connected to).

**One-time setup needed:** this repo needs its own `FIREBASE_SERVICE_ACCOUNT` secret added under Settings -> Secrets and variables -> Actions, using the same service account key already used in the `black94-app` repo (GitHub doesn't allow copying a secret's value between repos automatically - it has to be added here directly).

Once that's set, every push to `main` deploys automatically via `.github/workflows/deploy.yml`, or trigger it manually from the Actions tab.

## Updating privacy.html / terms.html

These are generated from the exact same content as the app's in-app legal screens (`lib/screens/legal_document_screen.dart` in the `black94-app` repo). If that content changes, regenerate these two files from there rather than hand-editing, to keep the in-app and web versions in sync.
