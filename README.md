# apps.nkreative.com

Static pages for NKreative's apps, served by GitHub Pages at `https://apps.nkreative.com`. Plain HTML and CSS, no build step, no cookies, analytics or third-party requests (fonts are bundled).

| Page | URL | File |
|---|---|---|
| Retrograde Privacy Policy | https://apps.nkreative.com/retrograde/privacy | `retrograde/privacy/index.html` |
| Retrograde Support | https://apps.nkreative.com/retrograde/support | `retrograde/support/index.html` |
| Retrograde landing | https://apps.nkreative.com/retrograde | `retrograde/index.html` |

`/retrograde/privacy` redirects to `/retrograde/privacy/` (GitHub Pages adds the trailing slash), so both forms work.

## Before publishing

1. Remove the yellow `<div class="draft">…</div>` banner and the `<meta name="robots" content="noindex">` line from every page.

## Publishing (GitHub Pages + Porkbun)

This only adds the `apps` subdomain; `nkreative.com` itself and its existing records stay as they are.

1. **GitHub:** create a public repository under the `Nkreative` account (for example `apps.nkreative.com`) and push this folder to its `main` branch.
2. **Pages:** repository Settings › Pages › Build and deployment: Source **Deploy from a branch**, branch **main**, folder **/ (root)**. The `CNAME` file sets the custom domain to `apps.nkreative.com`.
3. **Porkbun:** Domain Management › nkreative.com › DNS: add one record. Type **CNAME**, host **apps**, answer **nkreative.github.io**. Don't change the existing records for `nkreative.com` or `www`.
4. **Verify the domain (recommended):** GitHub › your account Settings › Pages › Add a domain › `nkreative.com`, then add the TXT record GitHub shows at Porkbun. This stops anyone else's repository from claiming an `nkreative.com` subdomain.
5. Once GitHub shows the DNS check as successful (DNS can take up to a day), tick **Enforce HTTPS**.
6. Open both URLs on an iPhone and check them.
7. **Then, in the Retrograde app:** set `AppLinks.privacyPolicy`, `AppLinks.supportPage` and `AppLinks.supportEmail` (`App/AppLinks.swift`), and enter the Privacy Policy URL and Support URL in App Store Connect › App Information.
