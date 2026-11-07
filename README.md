# dualnotes.app

The website for Dual Notes: a home page and the **Privacy Policy URL** that App Store Connect asks
for.

| Page | URL | Used for |
|---|---|---|
| `public/index.html` | https://dualnotes.app/ | Marketing URL (optional in App Store Connect) |
| `public/privacy/index.html` | https://dualnotes.app/privacy/ | Privacy Policy URL (required), and the link inside the app |

Plain HTML and one stylesheet. No build step, no scripts, no web fonts, no analytics — the privacy
page promises that nothing is collected, and the site keeps the same promise. `public/_headers`
sets a Content-Security-Policy that enforces it.

## Deploy

Cloudflare Pages, connected to this repository:

- Framework preset: **None**
- Build command: *(empty)*
- Build output directory: `public`
- Production branch: `main`

Every push to `main` deploys. The custom domain `dualnotes.app` is added under the Pages
project's **Custom domains**.

## Keeping the privacy page true

What `privacy/` says is what the app's own repo checks: `DrawEngineMono/PrivacyInfo.xcprivacy` and
`AppStoreSubmissionTests`. A version of the app that changes what it collects (analytics, an
account, a new permission) changes those, App Store Connect's App Privacy answer, and this page —
with a new date at its top — before that version ships.

## Preview locally

    python3 -m http.server --directory public 8000

then open http://localhost:8000/.
