# apps.nkreative.com

Static pages for NKreative's apps, served by GitHub Pages at `https://apps.nkreative.com`. Plain HTML and CSS, no build step, no cookies, analytics or third-party requests (fonts are bundled).

| Page | URL | File |
|---|---|---|
| Retrograde Privacy Policy | https://apps.nkreative.com/retrograde/privacy | `retrograde/privacy/index.html` |
| Retrograde Support | https://apps.nkreative.com/retrograde/support | `retrograde/support/index.html` |
| Retrograde landing | https://apps.nkreative.com/retrograde | `retrograde/index.html` |
| Between Lines Privacy Policy | https://apps.nkreative.com/between-lines/privacy | `between-lines/privacy/index.html` |
| Between Lines Support | https://apps.nkreative.com/between-lines/support | `between-lines/support/index.html` |
| Between Lines landing | https://apps.nkreative.com/between-lines | `between-lines/index.html` |

Retrograde's pages use `assets/site.css` (with the bundled fonts). Between Lines' pages use their own `between-lines/site.css` (system fonts, no font files), so changes to one app's styles never affect the other.

`/retrograde/privacy` redirects to `/retrograde/privacy/` (GitHub Pages adds the trailing slash), so both forms work.

## Publishing (GitHub Pages + Porkbun)

This only adds the `apps` subdomain; `nkreative.com` itself and its existing records stay as they are.

1. **GitHub:** create a public repository under the `Nkreative` account (for example `apps.nkreative.com`) and push this folder to its `main` branch.
2. **Pages:** repository Settings › Pages › Build and deployment: Source **Deploy from a branch**, branch **main**, folder **/ (root)**. The `CNAME` file sets the custom domain to `apps.nkreative.com`.
3. **Porkbun:** Domain Management › nkreative.com › DNS: add one record. Type **CNAME**, host **apps**, answer **nkreative.github.io**. Don't change the existing records for `nkreative.com` or `www`.
4. **Verify the domain (recommended):** GitHub › your account Settings › Pages › Add a domain › `nkreative.com`, then add the TXT record GitHub shows at Porkbun. This stops anyone else's repository from claiming an `nkreative.com` subdomain.
5. Once GitHub shows the DNS check as successful (DNS can take up to a day), tick **Enforce HTTPS**.
6. Open each app's URLs on an iPhone and check them.
7. **Then, in the Retrograde app:** set `AppLinks.privacyPolicy`, `AppLinks.supportPage` and `AppLinks.supportEmail` (`App/AppLinks.swift`), and enter the Privacy Policy URL and Support URL in App Store Connect › App Information.

### Adding Between Lines (domain already set up)

The `apps` subdomain, DNS and HTTPS are already in place, so publishing the `between-lines/` folder only needs a push to `main`. Then enter `https://apps.nkreative.com/between-lines/privacy/` as the Privacy Policy URL and `https://apps.nkreative.com/between-lines/support/` as the Support URL in App Store Connect › App Information for Between Lines. The web Privacy Policy must stay in step with the in-app policy (between-lines repo, `client/src/components/privacy-policy.tsx`): same facts, same "Last updated" date.
