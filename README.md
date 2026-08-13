# Rackside privacy policy site

Source for the public privacy policy that App Store Connect requires.

`index.html` is standalone — no build step, no dependencies. The app links to it
from **Settings → Privacy Policy** at:

```
https://benopp-app.github.io/rackside-privacy/
```

## Publishing (one-time)

This repo (`Rackside-app`) is private, and GitHub Pages will not serve a public
site from a private repo on the Free plan. So the policy lives in its own small
public repo, keeping the app source, build scripts, and curated datasets private.

1. Create a **public** repo named `rackside-privacy` under the `benopp-app` account.
   Do not add a README — it would conflict with the first push.

2. From this folder:

```bash
cd privacy-site
git init
git add index.html
git commit -m "Add Rackside privacy policy"
git branch -M main
git remote add origin https://github.com/benopp-app/rackside-privacy.git
git push -u origin main
```

3. In the new repo: **Settings → Pages → Source → Deploy from a branch**, branch
   `main`, folder `/ (root)`. Save.

4. Wait ~1 minute, then confirm the URL loads publicly — check it in a private
   window or on cellular, since being signed in can mask a permissions problem.

## Before App Store review

- [ ] `https://benopp-app.github.io/rackside-privacy/` loads while signed out
- [ ] `support@rackside.us` actually receives mail — the domain is referenced in
      the policy and Settings, and Apple does check that contact routes work
- [ ] The URL is entered in App Store Connect → App Information → Privacy Policy URL
- [ ] App Privacy questionnaire answered as **Data Not Collected**, which matches
      this policy and the code (no network calls, no analytics SDKs)

## Keeping it accurate

The policy makes specific factual claims — no network requests, no analytics, local
storage only, local notifications only. Those are true as of this commit and were
verified against the source. Re-check them if you ever add a dependency that talks
to a network, an analytics or crash-reporting SDK, remote push notifications, or
cloud sync. If any of those land, this policy and the App Privacy answers both
need updating before release.
