# mullensoft

Source repo for **mullensoft.com** — the landing / hub page for the fiddle app family.

## What this is

A static site (hand-written HTML/CSS, no build step yet) that:

- Presents the Mullensoft brand and the fiddle app family at the apex domain `mullensoft.com`.
- Links out to each app. Apps are served as GitHub Pages **project pages** under the `fiddle-app` account (e.g. `fiddle-app.github.io/ear`), so once `mullensoft.com` is attached to the family's Pages root they appear at `mullensoft.com/ear`, `/practice`, `/jam`, etc. — same bytes, branded host.

## Hosting decision (open)

This is the **source** repo (private). The **Pages/builds** target is still to be decided:

- For the apex-domain → app-subpath cascade to work, the Pages repo must be the **`fiddle-app.github.io` root repo** under the `fiddle-app` account. Attaching `mullensoft.com` there makes the apps' existing project pages resolve at `mullensoft.com/<app>` automatically — **no app migration**.
- A separate `mullensoft` GitHub **org** (broader publisher brand) remains an option for later; deferred deliberately. See the fiddle-family planning discussion.

## DNS / custom-domain checklist (do at launch)

1. Create the `fiddle-app.github.io` root repo (the landing build target) and enable Pages.
2. Add a `CNAME` file containing `mullensoft.com`.
3. At GoDaddy DNS, set the apex `A` records to GitHub Pages:
   - `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - (optional `AAAA` records for IPv6)
4. Add `www` `CNAME` → `fiddle-app.github.io`.
5. In repo Pages settings: set custom domain `mullensoft.com`, tick **Enforce HTTPS** once the cert provisions.
6. Verify the raw `fiddle-app.github.io/...` URLs 301-redirect to `mullensoft.com/...`.

## TODO before launch

- [ ] Adopt `_shared/design` tokens, fonts, and icons instead of the placeholder inline CSS in `index.html` (family reuse-from-start rule).
- [ ] Finalize app list, taglines, and per-app support/links.
- [ ] Decide source → Pages deploy path (reuse `scripts/deploy.sh` pattern vs. direct).
