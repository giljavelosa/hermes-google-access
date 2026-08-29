# hermes-google-access

Public OAuth information and privacy policy site for Gil's local Hermes Google
Workspace integration.

## Purpose

This repository contains the static informational site for **Hermes Google
Access**, a private, owner-operated local integration. It is **not** a public
SaaS product. Its sole purpose is to describe how the owner connects a locally
running Hermes Agent to his own Google Workspace data.

The site is hosted on GitHub Pages with a custom domain already configured in
the repository's GitHub Pages settings:

- **Homepage**: <https://google-access.omniscribeai.net/>
- **Privacy policy**: <https://google-access.omniscribeai.net/privacy/>

## Functionality

After explicit Google OAuth consent, the owner's local Hermes Agent may read,
search, and manage the following Google Workspace services, limited to the
owner's own data:

- **Gmail** — read, search, and manage email
- **Calendar** — view and manage events
- **Drive** — access and manage files
- **Docs** — view and edit documents
- **Sheets** — view and edit spreadsheets
- **Contacts** — view contact information only (optional, read-only, only if separately granted)

Access is granted only after the owner completes Google OAuth consent and may
be revoked at any time via <https://myaccount.google.com/permissions>.

## Local Preview

```bash
python3 -m http.server 8000
```

Then visit <http://localhost:8000> and <http://localhost:8000/privacy/>.

## Deployment

Deployment to GitHub Pages is automated via `.github/workflows/pages.yml`:

- **Trigger**: pushes to `main` and manual `workflow_dispatch`
- **Jobs**: `build` (stages `index.html`, `style.css`, `CNAME`, and
  `privacy/index.html` into `_site`, preserving the `privacy` directory, and
  uploads the artifact) and `deploy` (publishes to the `github-pages`
  environment)
- **Custom domain**: `google-access.omniscribeai.net`, set via the `CNAME` file
  and already configured in GitHub Pages settings

## DNS

The custom domain is served through a single DNS record managed at the
registrar:

- **CNAME** — host `google-access` → target `giljavelosa.github.io`

No nameserver delegation is involved.

## Google OAuth Configuration

- **Google authorized domain**: `omniscribeai.net`
- **Homepage URL**: `https://google-access.omniscribeai.net/`
- **Privacy policy URL**: `https://google-access.omniscribeai.net/privacy/`
- **Redirect**: the integration is a Desktop OAuth client and uses a local
  redirect; there is no hosted callback endpoint

## Privacy Policy

The full privacy policy is published at
<https://google-access.omniscribeai.net/privacy/>. It covers the data the local
integration accesses, purpose limitation, local storage of OAuth tokens,
limited sharing with owner-configured providers for explicit requests,
retention, and revocation.
